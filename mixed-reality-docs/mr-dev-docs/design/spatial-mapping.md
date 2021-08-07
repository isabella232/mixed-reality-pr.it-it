---
title: Mapping spaziale
description: La mappatura spaziale fornisce una rappresentazione dettagliata delle superfici reali nell'ambiente intorno HoloLens.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: mapping spaziale, HoloLens, realtà mista, ricostruzione della superficie, mesh, visore di realtà mista, visore windows di realtà mista, visore di realtà virtuale, HoloLens, MRTK, realtà mista Toolkit, comprensione della scena, world mesh, occlusione, fisica, navigazione, osservatore di superficie, rendering, elaborazione mesh
ms.openlocfilehash: 342ba116a5e33073acf2d4dbe563e74bccbf7053ec96d9b3f2f7ba88bd13da90
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212424"
---
# <a name="spatial-mapping"></a>Mapping spaziale

Il mapping spaziale offre una rappresentazione dettagliata delle superfici reali nell'ambiente intorno al HoloLens, consentendo agli sviluppatori di creare un'esperienza di realtà mista convincente. Unendo il mondo reale al mondo virtuale, un'applicazione può rendere gli ologrammi reali. Le applicazioni possono anche essere allineate in modo più naturale alle aspettative dell'utente fornendo comportamenti e interazioni reali familiari.

<br>

>[!VIDEO https://www.youtube.com/embed/zff2aQ1RaVo]

## <a name="device-supports"></a>Supporto del dispositivo

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Funzionalità</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens (prima generazione)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></td>
    </tr>
     <tr>
        <td>Mapping spaziale</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>


## <a name="why-is-spatial-mapping-important"></a>Perché il mapping spaziale è importante?

Il mapping spaziale consente di posizionare gli oggetti su superfici reali. In questo modo è possibile ancorare gli oggetti nel mondo dell'utente e sfruttare i segnali di profondità reali. Occluding your holograms based on other holograms and real world objects helps convince the user that these holograms are actually in their space. Ologrammi mobile nello spazio o lo spostamento con l'utente non sarà reale. Quando possibile, posizionare gli elementi per comodità.

Visualizzare le superfici durante il posizionamento o lo spostamento di ologrammi (usare una griglia proiettata). Ciò consente agli utenti di sapere dove possono posizionare meglio gli ologrammi e indica se il punto in cui sta tentando di posizionare l'ologramma non è mappato. È possibile "creare un manifesto" verso l'utente se finisce con un angolo troppo alto.

## <a name="conceptual-overview"></a>Panoramica dei concetti

![Superfici mesh che coprono una stanza](images/SurfaceReconstruction.jpg)<br>
*Esempio di mesh di mapping spaziale che copre una stanza*

I due tipi di oggetto principali usati per il mapping spaziale sono "Spatial Surface Observer" e "Spatial Surface".

L'applicazione fornisce a Spatial Surface Observer uno o più volumi di delimitazione, per definire le aree di spazio in cui l'applicazione vuole ricevere i dati di mapping spaziale. Per ognuno di questi volumi, il mapping spaziale fornirà all'applicazione un set di superfici spaziali.

Questi volumi possono essere fissi (in una posizione fissa basata sul mondo reale) o possono essere collegati al HoloLens (si spostano, ma non ruotano, con il HoloLens mentre si sposta nell'ambiente). Ogni superficie spaziale descrive le superfici reali in un piccolo volume di spazio, rappresentato come una mesh triangolare collegata a un sistema di [coordinate spaziali bloccato dal mondo.](coordinate-systems.md)

Quando il HoloLens raccoglie nuovi dati sull'ambiente e con le modifiche apportate all'ambiente, le superfici spaziali vengono visualizzate, scompaiono e cambiano.

## <a name="spatial-awareness-design-concepts-demo"></a>Demo dei concetti di progettazione della consapevolezza spaziale

Se si desidera vedere i concetti di progettazione della consapevolezza spaziale in azione, vedere la demo video **progettazione Ologrammi - Consapevolezza** spaziale di seguito. Al termine, continuare per un'analisi più dettagliata di argomenti specifici.

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Spatial-Awareness-Chapter/player]

*Questo video è stato tratto dall'app "Progettazione Ologrammi" HoloLens 2 app. Scaricare e usufruire dell'esperienza completa [qui.](https://aka.ms/dhapp)*

## <a name="spatial-mapping-vs-scene-understanding-worldmesh"></a>Mapping spaziale e Comprensione scena WorldMesh

Ad HoloLens 2, è possibile eseguire una query su una versione statica dei dati di mapping spaziale usando [Scene Understanding SDK](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md) (impostazione EnableWorldMesh). Ecco le differenze tra due modi per accedere ai dati di mapping spaziale:
* API Mapping spaziale:
   * Intervallo limitato: i dati di mapping spaziale disponibili per le applicazioni in una "bolla" memorizzata nella cache di dimensioni limitate intorno all'utente.
   * Fornisce aggiornamenti a bassa latenza delle aree mesh modificate tramite gli eventi SurfacesChanged.
   * Livello variabile di dettagli controllato dal parametro Triangles Per Cubic Meter.
* SDK di comprensione della scena:
   * Intervallo illimitato: fornisce tutti i dati di mapping spaziale analizzati all'interno del raggio della query.
   * Fornisce uno snapshot statico dei dati di mapping spaziale. Per ottenere i dati aggiornati del mapping spaziale, è necessario eseguire una nuova query per l'intera mesh.
   * Livello coerente di dettagli controllato dall'impostazione RequestedMeshLevelOfDetail.

## <a name="what-influences-spatial-mapping-quality"></a>Cosa influisce sulla qualità del mapping spaziale?

Diversi fattori, qui [dettagliati,](/hololens/hololens-environment-considerations)possono influire sulla frequenza e sulla gravità di questi errori.  È tuttavia consigliabile progettare l'applicazione in modo che l'utente possa raggiungere i propri obiettivi anche in presenza di errori nei dati di mapping spaziale.

## <a name="common-usage-scenarios"></a>Scenari di utilizzo comuni

![Illustrazioni di scenari di utilizzo comuni di Mapping spaziale: posizionamento, occlusione, fisica e navigazione](images/sm-concepts-1000px.png)

### <a name="placement"></a>Selezione host

La mappatura spaziale offre alle applicazioni la possibilità di presentare forme di interazione naturali e familiari all'utente; cosa potrebbe essere più naturale rispetto all'inserimento del telefono sulla scrivania?

Vincolare il posizionamento degli ologrammi (o, più in generale, qualsiasi selezione di posizioni spaziali) su superfici offre un mapping naturale da 3D (punto nello spazio) a 2D (punto sulla superficie). In questo modo si riduce la quantità di informazioni che l'utente deve fornire all'applicazione e rende le interazioni dell'utente più veloci, più semplici e precise. Questo è vero perché "distanza" non è qualcosa che viene usato per comunicare fisicamente con altre persone o con i computer. Quando si punta con il dito, si specifica una direzione ma non una distanza.

Un'importante avvertenza è che quando un'applicazione deduce la distanza dalla direzione (ad esempio eseguendo un raycast lungo la direzione dello sguardo dell'utente per trovare la superficie spaziale più vicina), questo deve produrre risultati che l'utente può stimare in modo affidabile. In caso contrario, l'utente perderà il controllo e questo può diventare rapidamente frustrante. Un metodo utile per questo scopo è eseguire più raycast anziché uno solo. I risultati dell'aggregazione devono essere più fluidi e prevedibili, meno soggetti all'influenza dei risultati temporanei di "outlier", come può essere causato da raggi che passano attraverso piccoli fori o che toccano piccole porzioni di geometria che l'utente non conosce. L'aggregazione o l'arrotondamento possono essere eseguiti anche nel tempo. Ad esempio, è possibile limitare la velocità massima a cui un ologramma può variare a distanza dall'utente. È anche possibile limitare il valore minimo e massimo della distanza, in modo che l'ologramma spostato non si all'improvviso voli in lontananza o si arresti di nuovo nel viso dell'utente.

Le applicazioni possono anche usare la forma e la direzione delle superfici per guidare il posizionamento dell'ologramma. Una cattedra olografica non deve penetrare attraverso le pareti e deve essere arrossata con il pavimento anche se è leggermente irregolare. Questo tipo di funzionalità probabilmente si baserebbe sull'uso di collisioni fisiche anziché di raycast, ma si applicano problemi simili. Se l'ologramma posizionato ha molti piccoli poligoni che si espandono, ad esempio le cosce su una cattedra, può essere opportuno espandere la rappresentazione fisica di questi poligoni a qualcosa di più ampio e levigato in modo che siano più in grado di scorrere sulle superfici spaziali senza intoppi.

In estrema analisi, l'input dell'utente può essere semplificato completamente e le superfici spaziali possono essere usate per eseguire il posizionamento ologramma completamente automatico. Ad esempio, l'applicazione potrebbe posizionare un interruttore di luce olografico da qualche parte sulla parete in modo che l'utente possa premere. La stessa avvertenza sulla prevedibilità si applica doppiamente qui; se l'utente si aspetta il controllo sul posizionamento dell'ologramma, ma l'applicazione non posiziona sempre gli ologrammi nel punto previsto (se il commutatore di luce viene visualizzato in un punto in cui l'utente non può raggiungere), si tratta di un'esperienza frustrante. In realtà può essere peggiore eseguire il posizionamento automatico che richiede la correzione dell'utente in parte, piuttosto che richiedere all'utente di eseguire sempre il posizionamento; poiché è previsto un corretto *posizionamento* automatico, la correzione manuale sembra un onere.

Si noti anche che la possibilità di un'applicazione di usare superfici spaziali per il posizionamento dipende in gran parte dall'esperienza di [analisi dell'applicazione.](spatial-mapping.md#the-environment-scanning-experience) Se una superficie non è stata analizzata, non può essere usata per il posizionamento. L'applicazione deve chiarirlo all'utente, in modo che possa analizzare nuove superfici o selezionare una nuova posizione.

Il feedback visivo per l'utente è di importanza fondamentale durante il posizionamento. L'utente deve sapere dove si basa l'ologramma sulla superficie più vicina con [effetti di messa a terra.](spatial-mapping.md#visualization) Devono comprendere perché lo spostamento dell'ologramma è vincolato (ad esempio, a causa di collisioni con un'altra superficie vicina). Se non possono inserire un ologramma nella posizione corrente, il feedback visivo dovrebbe chiarire perché no. Ad esempio, se l'utente sta tentando di posizionare un divano olografico bloccato a metà strada nella parete, le parti del divano che si trova dietro la parete dovrebbero pulsare in un colore adirato. Al contrario, se l'applicazione non trova una superficie spaziale in una posizione in cui l'utente può visualizzare una superficie reale, l'applicazione deve chiarire questo punto. L'ovvia assenza di un effetto di messa a terra in questo settore può raggiungere questo scopo.

### <a name="occlusion"></a>Occlusione

Uno degli usi principali delle superfici di mapping spaziale è semplicemente occludere gli ologrammi. Questo comportamento semplice ha un impatto enorme sul realistico percepito degli ologrammi, contribuendo a creare un senso viscerale che in realtà si annida nello stesso spazio fisico dell'utente.

Occlusion fornisce anche informazioni all'utente. Quando un ologramma sembra essere occluso da una superficie reale, questo fornisce un feedback visivo aggiuntivo sulla posizione spaziale di tale ologramma nel mondo. Al contrario, l'occlusione può anche nascondere in modo utile *le* informazioni all'utente. Ologrammi occluding dietro le pareti possono ridurre l'ingombro visivo in modo intuitivo. Per nascondere o rivelare un ologramma, l'utente deve semplicemente spostare la testa.

L'occlusione può essere usata anche per creare aspettative per un'interfaccia utente naturale basata su interazioni fisiche familiari. Se un ologramma è occluso da una superficie, è perché tale superficie è solida, quindi l'utente deve aspettarsi che l'ologramma *colliderà* con tale superficie e non passerà attraverso di essa.

A volte, l'occlusione degli ologrammi non è desiderabile. Se un utente deve interagire con un ologramma, deve vederlo, anche se si trova dietro una superficie reale. In questi casi, in genere è opportuno eseguire il rendering di un ologramma in modo diverso quando è occluso (ad esempio, riducendone la luminosità). In questo modo, l'utente può individuare visivamente l'ologramma, ma saprà comunque che si trova dietro qualcosa.

### <a name="physics"></a>Fisica

L'uso della simulazione fisica è un altro modo  in cui il mapping spaziale può essere usato per rafforzare la presenza di ologrammi nello spazio fisico dell'utente. Quando la palla di gomma olografica rotola in modo realistico dalla scrivania, rimbalza sul pavimento e scompare sotto il divano, potrebbe essere difficile per me pensare che non ci sia.

La simulazione fisica offre anche l'opportunità a un'applicazione di usare interazioni naturali e familiari basate sulla fisica. Lo spostamento di un mobile olografico sul pavimento sarà probabilmente più semplice per l'utente se il mobile risponde come se fosse scorrevole sul pavimento con l'inerzia e l'attrito appropriati.

Per generare comportamenti fisici realistici, è probabile che sia necessario eseguire alcune operazioni di elaborazione della [mesh,](spatial-mapping.md#mesh-processing) ad esempio il riempimento dei fori, la rimozione di allucinazioni mobili e l'arrotondamento di superfici ruvide.

È anche necessario considerare il modo in cui l'esperienza di analisi dell'applicazione [influisce](spatial-mapping.md#the-environment-scanning-experience) sulla simulazione fisica. In primo luogo, le superfici mancanti non si scontrano con nulla; cosa accade quando la palla di gomma scende dal modellatore e dalla fine del mondo noto? In secondo luogo, è necessario decidere se si continuerà a rispondere alle modifiche nell'ambiente nel tempo. In alcuni casi, è necessario rispondere il più rapidamente possibile. ad esempio se l'utente usa porte e mobili come barricate mobili in difesa da una tempesta di frecce romane in ingresso. In altri casi, tuttavia, potrebbe essere necessario ignorare i nuovi aggiornamenti. guidare l'auto olografica intorno all'auto da corsa sul pavimento potrebbe improvvisamente non essere così divertente se il cane decide di sedersi al centro della traccia.

### <a name="navigation"></a>Spostamento

Le applicazioni possono usare i dati di mapping spaziale per concedere ai caratteri olografici (o agli agenti) la possibilità di spostarsi nel mondo reale nello stesso modo di una persona reale. Ciò consente di rafforzare la presenza di caratteri olografici limitandoli allo stesso set di comportamenti naturali e familiari di quelli dell'utente e dei loro amici.

Le funzionalità di navigazione possono essere utili anche per gli utenti. Dopo che una mappa di navigazione è stata compilata in una determinata area, può essere condivisa per fornire indicazioni olografiche per i nuovi utenti che non hanno familiarità con tale posizione. Questa mappa può essere progettata per mantenere fluido il flusso del traffico pedonale o per evitare incidenti in posizioni pericolose come i cantiere.

Le principali sfide tecniche legate all'implementazione della funzionalità di navigazione saranno il rilevamento affidabile delle superfici a piedi (gli esseri umani non passano sulle tabelle) e l'adattamento alle modifiche dell'ambiente (gli esseri umani non attraversano porte chiuse). La mesh può richiedere alcune [elaborazioni](spatial-mapping.md#mesh-processing) prima che sia utilizzabile per la pianificazione del percorso e la navigazione da parte di un carattere virtuale. L'arrotondamento della mesh e la rimozione delle allucinazioni possono aiutare a evitare che i caratteri si bloccano. È anche possibile semplificare drasticamente la mesh per velocizzare la pianificazione del percorso e i calcoli di navigazione del personaggio. Queste sfide hanno ricevuto una grande attenzione nello sviluppo della tecnologia dei videogiochi e sono disponibili numerose pubblicazioni di ricerca su questi argomenti.

La funzionalità NavMesh incorporata in Unity non può essere usata con le superfici di mapping spaziale. Ciò è dovuto al fatto che le superfici di mapping spaziale non sono note fino all'avvio dell'applicazione, ma i file di dati NavMesh devono essere generati in anticipo dagli asset di origine. Si noti anche che il sistema [](spatial-mapping.md#the-environment-scanning-experience) di mapping spaziale non fornirà informazioni sulle superfici lontano dalla posizione corrente dell'utente. L'applicazione deve quindi "ricordare" le superfici se si tratta di creare una mappa di un'area di grandi dimensioni.

### <a name="visualization"></a>Visualizzazione

Nella maggior parte dei casi è appropriato che le superfici spaziali siano invisibili; per ridurre al minimo il disordine visivo e consentire al mondo reale di parlare da solo. Tuttavia, a volte è utile visualizzare direttamente le superfici di mapping spaziale, nonostante le controparti reali siano visibili.

Ad esempio, quando l'utente sta provando a posizionare un ologramma su una superficie (ad esempio, posizionando un mobile olografico sulla parete), può essere utile "mettere a terra" l'ologramma proiettando un'ombreggiatura sulla superficie. In questo modo l'utente ha un senso molto più chiaro della prossimità fisica esatta tra l'ologramma e la superficie. Questo è anche un esempio della pratica più generale di "visualizzare in anteprima" visivamente una modifica prima che l'utente eserciti il commit.

Visualizzando le superfici, l'applicazione può condividere con l'utente la comprensione dell'ambiente. Ad esempio, un gioco da tavolo olografico potrebbe visualizzare le superfici orizzontali identificate come "tabelle", in modo che l'utente sappia dove deve interagire.

La visualizzazione delle superfici può essere un modo utile per visualizzare gli spazi vicini dell'utente nascosti alla visualizzazione. Questo potrebbe fornire un modo per consentire all'utente di accedere alla propria cucina (e a tutti gli ologrammi contenuti) dal proprio living.

Le mesh di superficie fornite dal mapping spaziale potrebbero non essere particolarmente "pulite". È importante visualizzarle in modo appropriato. I calcoli dell'illuminazione tradizionali possono evidenziare gli errori nelle normali della superficie in modo visivamente distratto, mentre le trame "pulite" proiettate sulla superficie possono contribuire a dare un aspetto più ordinato. È anche possibile eseguire l'elaborazione [della mesh](spatial-mapping.md#mesh-processing) per migliorare le proprietà della mesh, prima del rendering delle superfici.

> [!NOTE]
> HoloLens 2 implementa un nuovo [runtime scene understanding](scene-understanding.md)che fornisce agli sviluppatori di realtà mista una rappresentazione dell'ambiente strutturata di alto livello progettata per semplificare l'implementazione di posizionamento, occlusione, fisica e navigazione.

## <a name="using-the-surface-observer"></a>Uso di Surface Observer

Il punto di partenza per il mapping spaziale è l'osservatore di superficie. Il flusso del programma è il seguente:
* Creare un oggetto osservatore di superficie
   * Specificare uno o più volumi spaziali per definire le aree di interesse in cui l'applicazione desidera ricevere i dati di mapping spaziale. Un volume spaziale è semplicemente una forma che definisce un'area di spazio, ad esempio una sfera o una casella.
   * Usare un volume spaziale con un sistema di coordinate spaziali bloccato dal mondo per identificare un'area fissa del mondo fisico.
   * Usare un volume spaziale, aggiornato ogni fotogramma con un sistema di coordinate spaziali bloccato dal corpo, per identificare un'area di spazio che si sposta (ma non ruota) con l'utente.
   * Questi volumi spaziali possono essere modificati in un secondo momento in qualsiasi momento, quando lo stato dell'applicazione o dell'utente cambia.
* Usare il polling o la notifica per recuperare informazioni sulle superfici spaziali
   * È possibile "eseguire il polling" dell'osservatore di superficie per lo stato della superficie spaziale in qualsiasi momento. È invece possibile registrarsi per l'evento "Surfaces changed" dell'osservatore di superficie, che invierà una notifica all'applicazione quando le superfici spaziali sono state modificate.
   * Per un volume spaziale dinamico, ad esempio il frustum di visualizzazione o un volume bloccato dal corpo, le applicazioni dovranno eseguire il polling delle modifiche per ogni fotogramma impostando l'area di interesse e quindi ottenendo il set corrente di superfici spaziali.
   * Per un volume statico, ad esempio un cubo bloccato dal mondo che copre una singola stanza, le applicazioni possono registrarsi per l'evento "surfaces changed" per ricevere una notifica quando le superfici spaziali all'interno di tale volume potrebbero essere cambiate.
* Elaborare le modifiche delle superfici
   * Scorrere il set specificato di superfici spaziali.
   * Classificare le superfici spaziali come aggiunte, modificate o rimosse.
   * Per ogni superficie spaziale aggiunta o modificata, se appropriato inviare una richiesta asincrona per ricevere una mesh aggiornata che rappresenta lo stato corrente della superficie al livello di dettaglio desiderato.
* Elaborare la richiesta di mesh asincrona (altre informazioni nelle sezioni seguenti).

## <a name="mesh-caching"></a>Modello Caching

Le superfici spaziali sono rappresentate da mesh a triangolo denso. L'archiviazione, il rendering e l'elaborazione di queste mesh possono utilizzare risorse di calcolo e di archiviazione significative. Di conseguenza, ogni applicazione deve adottare uno schema di memorizzazione nella cache della mesh appropriato alle proprie esigenze, per ridurre al minimo le risorse usate per l'elaborazione e l'archiviazione della mesh. Questo schema deve determinare quali mesh mantenere e quali rimuovere e quando aggiornare la mesh per ogni superficie spaziale.

Molte delle considerazioni illustrate in questo argomento informeranno direttamente come l'applicazione deve approcciare la memorizzazione nella cache mesh. È necessario considerare il modo in cui l'utente passa attraverso l'ambiente, quali superfici sono necessarie, quando verranno osservate superfici diverse e quando devono essere acquisite le modifiche nell'ambiente.

Quando si interpreta l'evento "surfaces changed" fornito dall'osservatore di superficie, la logica di memorizzazione nella cache della mesh di base è la seguente:
* Se l'applicazione visualizza un ID di superficie spaziale che non ha mai visto in precedenza, deve considerarlo come una nuova superficie spaziale.
* Se l'applicazione vede una superficie spaziale con un ID noto ma con un nuovo tempo di aggiornamento, deve considerarla come una superficie spaziale aggiornata.
* Se l'applicazione non vede più una superficie spaziale con un ID noto, deve considerarla come una superficie spaziale rimossa.

Ogni applicazione può quindi effettuare le scelte seguenti:It's up to each application to then make the following choices:
* Per le nuove superfici spaziali, è necessario che sia richiesta la mesh?
   * In genere la mesh deve essere richiesta immediatamente per le nuove superfici spaziali, che possono fornire nuove informazioni utili all'utente.
   * Tuttavia, alle nuove superfici spaziali vicino e davanti all'utente deve essere data priorità e la mesh deve essere richiesta per prima.
   * Se la nuova mesh non è necessaria, se, ad esempio, l'applicazione ha bloccato in modo permanente o temporaneo il modello dell'ambiente, non deve essere richiesta.
* Per le superfici spaziali aggiornate, è necessario che sia richiesta la mesh?
   * Le superfici spaziali aggiornate vicino e davanti all'utente devono avere la priorità e la mesh deve essere richiesta per prima.
   * Può anche essere opportuno assegnare una priorità più elevata alle nuove superfici rispetto alle superfici aggiornate, in particolare durante l'esperienza di analisi.
   * Per limitare i costi di elaborazione, le applicazioni possono voler limitare la frequenza con cui elaborano gli aggiornamenti alle superfici spaziali.
   * Potrebbe essere possibile dedurre che le modifiche a una superficie spaziale sono secondarie, ad esempio se i limiti della superficie sono piccoli, nel qual caso l'aggiornamento potrebbe non essere sufficientemente importante da elaborare.
   * Gli aggiornamenti alle superfici spaziali esterne all'area corrente di interesse dell'utente possono essere ignorati completamente, anche se in questo caso può essere più efficiente modificare i volumi di delimitazione spaziali in uso dall'osservatore di superficie.
* Per le superfici spaziali rimosse, la mesh deve essere eliminata?
   * In genere la mesh deve essere eliminata immediatamente per le superfici spaziali rimosse, in modo che l'occlusione dell'ologramma rimanga corretta.
   * Tuttavia, se l'applicazione ha motivo di ritiene che una superficie spaziale riapparirà a breve (in base alla progettazione dell'esperienza utente), potrebbe essere più efficiente mantenerla piuttosto che eliminare la mesh e ricrearla di nuovo in un secondo momento.
   * Se l'applicazione sta creando un modello su larga scala dell'ambiente dell'utente, potrebbe non voler eliminare alcuna mesh. Sarà comunque necessario limitare l'utilizzo delle risorse, possibilmente tramite lo spooling delle mesh su disco quando le superfici spaziali scompaiono.
   * Alcuni eventi relativamente rari durante la generazione di superfici spaziali possono causare la sostituzione delle superfici spaziali con nuove superfici spaziali in una posizione simile ma con ID diversi. Pertanto, le applicazioni che scelgono di non eliminare una superficie rimossa devono fare attenzione a non finire con più mesh di superfici spaziali altamente sovrapposte che coprono la stessa posizione.
* La mesh deve essere eliminata per altre superfici spaziali?
   * Anche se esiste una superficie spaziale, se non è più utile per l'esperienza dell'utente, deve essere eliminata. Ad esempio, se l'applicazione "sostituisce" la stanza sull'altro lato di una porta con uno spazio virtuale alternativo, le superfici spaziali in tale stanza non sono più importanti.

Ecco una strategia di memorizzazione nella cache mesh di esempio, che usa l'isteria spaziale e temporale:
* Si consideri un'applicazione che vuole usare un volume spaziale a forma di frustum di interesse che segue lo sguardo dell'utente mentre si guarda intorno e si aggira.
* Una superficie spaziale può scomparire temporaneamente da questo volume semplicemente perché l'utente si allontana dalla superficie o si allontana da esso... solo per guardare indietro o avvicinarsi di nuovo un momento dopo. In questo caso, l'eliminazione e la nuova creazione della mesh per questa superficie rappresentano molte elaborazioni ridondanti.
* Per ridurre il numero di modifiche elaborate, l'applicazione usa due osservatori della superficie spaziale, uno contenuto all'interno dell'altro. Il volume più grande è sferico e segue l'utente "lazily"; si sposta solo quando necessario per assicurarsi che il centro si trova entro 2,0 metri dall'utente.
* Le mesh di superficie spaziale nuove e aggiornate vengono sempre elaborate dall'osservatore della superficie interna più piccola, ma le mesh vengono memorizzate nella cache fino a quando non scompaiono dall'osservatore della superficie esterna più grande. Ciò consente all'applicazione di evitare l'elaborazione di molte modifiche ridondanti a causa dello spostamento dell'utente locale.
* Poiché una superficie spaziale può anche scomparire temporaneamente a causa della perdita di rilevamento, l'applicazione rinvia anche la rimozione delle superfici spaziali rimosse durante la perdita di rilevamento.
* In generale, un'applicazione deve valutare il compromesso tra una riduzione dell'elaborazione degli aggiornamenti e un maggiore utilizzo della memoria per determinare la strategia di memorizzazione nella cache ideale.

## <a name="rendering"></a>Rendering

Esistono tre modi principali in cui le mesh di mapping spaziale tendono a essere usate per il rendering:
* Per la visualizzazione della superficie
   * Spesso è utile visualizzare direttamente le superfici spaziali. Ad esempio, il cast di "ombreggiature" da oggetti su superfici spaziali può fornire un feedback visivo utile all'utente mentre posiziona ologrammi sulle superfici.
   * Un aspetto da tenere presente è che le mesh spaziali sono diverse dal tipo di mesh che un artista 3D potrebbe creare. La topologia a triangolo non sarà "pulita" come la topologia creata dall'utente e la mesh subirà [vari errori.](spatial-mapping.md#what-influences-spatial-mapping-quality)
   * Per creare un aspetto visivo gradevole, è possibile eseguire alcune operazioni di elaborazione [mesh,](spatial-mapping.md#mesh-processing)ad esempio per riempire fori o normali della superficie uniformi. È anche possibile usare uno shader per proiettare trame progettate dall'artista nella mesh invece di visualizzare direttamente la topologia e le normali della mesh.
* Per ologrammi occlusi dietro superfici reali
   * È possibile eseguire il rendering delle superfici spaziali in un passaggio solo di profondità, che influisce solo sul [buffer](/windows/win32/direct3d9/depth-buffers) di profondità e non sulle destinazioni di rendering dei colori.
   * In questo modo il buffer di profondità viene prime per occludere gli ologrammi sottoposti successivamente a rendering dietro le superfici spaziali. L'occlusione accurata degli ologrammi migliora il senso che gli ologrammi esistano realmente all'interno dello spazio fisico dell'utente.
   * Per abilitare il rendering solo profondità, aggiornare lo stato di blend per impostare [RenderTargetWriteMask](/windows/win32/api/d3d11_1/ns-d3d11_1-d3d11_render_target_blend_desc1) su zero per tutte le destinazioni di rendering dei colori.
* Per modificare l'aspetto degli ologrammi occlusi da superfici reali
   * In genere la geometria sottoposta a rendering è nascosta quando è occlusa. A tale scopo, impostare la funzione di profondità nello stato [depth-stencil](/windows/win32/api/d3d11/ns-d3d11-d3d11_depth_stencil_desc) su "minore o uguale  a", in modo che la geometria sia visibile solo dove è più vicina alla fotocamera rispetto a tutte le geometrie di cui è stato eseguito il rendering in precedenza.
   * Tuttavia, può essere utile mantenere visibile una determinata geometria anche quando è occlusa e modificarne l'aspetto quando è occluso come modo per fornire feedback visivo all'utente. Ad esempio, in questo modo l'applicazione può mostrare all'utente la posizione di un oggetto, rendendo chiaro che si trova dietro una superficie reale.
   * A tale scopo, eseguire il rendering della geometria una seconda volta con uno shader diverso che crea l'aspetto desiderato "occluded". Prima di eseguire il rendering della geometria per la seconda volta, apportare due modifiche allo [stato depth-stencil](/windows/win32/api/d3d11/ns-d3d11-d3d11_depth_stencil_desc). Impostare prima di tutto la funzione depth su "greater than or equal"  in modo che la geometria sia visibile solo dove si trova oltre la fotocamera rispetto a tutte le geometrie di cui è stato eseguito il rendering in precedenza. In secondo momento, impostare DepthWriteMask su zero, in modo che il buffer di profondità non  verrà modificato (il buffer di profondità deve continuare a rappresentare la profondità della geometria più vicina alla fotocamera).

[Le prestazioni](../develop/platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md) sono un problema importante quando si esegue il rendering di mesh di mapping spaziale. Ecco alcune tecniche di prestazioni di rendering specifiche per il rendering di mesh di mapping spaziale:
* Regolare la densità del triangolo
   * Quando si richiedono mesh di superficie spaziale all'osservatore di superficie, richiedere la densità più bassa di mesh triangolare che saranno sufficiente per le proprie esigenze.
   * Può essere opportuno variare la densità del triangolo su una superficie in base alla superficie, a seconda della distanza della superficie dall'utente e della pertinenza dell'esperienza utente.
   * La riduzione del numero di triangoli ridurrà l'utilizzo della memoria e i costi di elaborazione dei vertici nella GPU, anche se non influiranno sui costi di elaborazione dei pixel.
* Usare il frustum culling
   * Il frustum culling ignora gli oggetti di disegno che non possono essere visualizzati perché sono esterni al frustum di visualizzazione corrente. In questo modo si riducono sia i costi di elaborazione della CPU che della GPU.
   * Poiché il culling viene eseguito in base alla mesh e le superfici spaziali possono essere grandi, suddividere ogni mesh di superficie spaziale in blocchi più piccoli può comportare un culling più efficiente (in quanto viene eseguito il rendering di un minor numero di triangoli fuori schermo). Esiste tuttavia un compromesso. Maggiore è il numero di mesh, maggiore è il numero di chiamate di disegno che è necessario effettuare, che possono aumentare i costi della CPU. In casi estremi, i calcoli di frustum culling potrebbero anche avere un costo misurabile della CPU.
* Regolare l'ordine di rendering
   * Le superfici spaziali tendono a essere grandi, perché rappresentano l'intero ambiente dell'utente che le circonda. I costi di elaborazione dei pixel nella GPU possono essere elevati, soprattutto nei casi in cui è presente più di un livello di geometria visibile (incluse le superfici spaziali e altri ologrammi). In questo caso, il livello più vicino all'utente occluderà tutti i livelli più lontano, quindi qualsiasi tempo di GPU impiegato per il rendering di questi livelli più distanti viene sprecato.
   * Per ridurre questo lavoro ridondante sulla GPU, è utile eseguire il rendering di superfici opache in ordine front-to-back (quelle più vicine per prime, più distanti per ultime). Per "opaco" si intende una superficie per cui DepthWriteMask è impostato su uno nello [stato depth-stencil.](/windows/win32/api/d3d11/ns-d3d11-d3d11_depth_stencil_desc) Quando viene eseguito il rendering delle superfici più vicine, il buffer di profondità viene eseguito in modo che le superfici più distanti siano ignorate in modo efficiente dal processore di pixel nella GPU.

## <a name="mesh-processing"></a>Elaborazione mesh

Un'applicazione potrebbe voler eseguire [varie operazioni sulle](spatial-mapping.md#mesh-processing) mesh della superficie spaziale in base alle proprie esigenze. I dati dell'indice e dei vertici forniti con ogni mesh della superficie spaziale utilizzano lo stesso layout familiare dei [buffer](/windows/win32/direct3d9/rendering-from-vertex-and-index-buffers) di vertici e indici usati per il rendering delle mesh triangolare in tutte le API di rendering moderne. Tuttavia, un fatto fondamentale da tenere presente è che i triangoli di mapping spaziale hanno un ordine di avvolgimento anteriore in **senso orario.** Ogni triangolo è rappresentato da tre indici dei vertici nel index buffer della mesh e questi indici  identificheranno i vertici del  triangolo in senso orario, quando il triangolo viene visualizzato dal lato anteriore. Il lato anteriore (o esterno) delle mesh della superficie spaziale corrisponde come ci si aspetterebbe al lato anteriore (visibile) delle superfici reali.

Le applicazioni devono eseguire la semplificazione della mesh solo se la densità del triangolo più grossolano fornita dall'osservatore di superficie è ancora sufficientemente grossolano. Questo lavoro è dispendioso dal punto di vista del calcolo e viene già eseguito dal runtime per generare i vari livelli di dettaglio forniti.

Poiché ogni osservatore di superficie può fornire più superfici spaziali non interconnesse, alcune applicazioni potrebbero voler ritagliare queste mesh di superficie spaziale l'una contro l'altra e quindi comprimerle insieme. In generale, il passaggio di ritaglio è obbligatorio, perché le mesh della superficie spaziale nelle vicinanze spesso si sovrappongono leggermente.

## <a name="raycasting-and-collision"></a>Raycasting e collisione

Per consentire a un'API fisica (ad esempio [Havok)](https://www.havok.com/)di fornire a un'applicazione funzionalità di raycasting e collisione per le superfici spaziali, l'applicazione deve fornire mesh di superficie spaziale all'API fisica. Le mesh usate per la fisica hanno spesso le proprietà seguenti:
* Contengono solo un numero ridotto di triangoli. Le operazioni fisiche sono più a elevato utilizzo di calcolo rispetto alle operazioni di rendering.
* Sono "molto compatte". Le superfici destinate a essere solide non devono contenere piccoli fori. anche fori troppo piccoli per essere visibili possono causare problemi.
* Vengono convertiti in scafi convessi. Gli scafi convessi hanno pochi poligoni e sono senza fori e sono molto più efficienti dal punto di vista computazionale rispetto alle mesh di triangoli non elaborati.

Quando si esetterano raycast su superfici spaziali, tenere presente che queste superfici sono spesso complesse e ingombrate con pochi dettagli, proprio come la tua scriva! Ciò significa che un singolo raycast spesso non è sufficiente per fornire informazioni sufficienti sulla forma della superficie e sulla forma dello spazio vuoto nelle vicinanze. È in genere una buona idea eseguire molti raycast all'interno di una piccola area e usare i risultati aggregati per ottenere una comprensione più affidabile della superficie. Ad esempio, se si usa la media di 10 raycast per guidare il posizionamento degli ologrammi su una superficie, si otterranno risultati molto più uniformi e meno "instabilità" rispetto all'uso di un singolo raycast.

Tenere tuttavia presente che ogni raycast può avere un costo di calcolo elevato. A seconda dello scenario di utilizzo, è consigliabile trovare un compromesso tra il costo [](spatial-mapping.md#mesh-processing) di calcolo dei raycast aggiuntivi (eseguito ogni fotogramma) e il costo di calcolo dell'elaborazione mesh per uniformare e rimuovere i fori nelle superfici spaziali (operazione eseguita quando vengono aggiornate le mesh spaziali).

## <a name="the-environment-scanning-experience"></a>Esperienza di analisi dell'ambiente

Ogni applicazione che usa il mapping spaziale deve considerare la possibilità di offrire un'esperienza di analisi. processo tramite il quale l'applicazione guida l'utente nell'analisi delle superfici necessarie per il corretto funzionamento dell'applicazione.

![Esempio di analisi](images/sr-mixedworld-140429-8pm-00068-1000px.png)<br>
*Esempio di analisi*

La natura di questa esperienza di analisi può variare notevolmente a seconda delle esigenze di ogni applicazione, ma due principi principali dovrebbero guidarne la progettazione.

In primo luogo, **una comunicazione chiara con l'utente è il problema principale.** L'utente deve sempre sapere se vengono soddisfatti i requisiti dell'applicazione. Quando non vengono soddisfatti, dovrebbe essere immediatamente chiaro all'utente il motivo per cui si tratta di questa condizione e devono essere in grado di eseguire rapidamente l'azione appropriata.

In secondo **luogo, le applicazioni devono tentare di trovare un equilibrio tra efficienza e affidabilità**. Quando è possibile eseguire questa operazione **in** modo affidabile, le applicazioni devono analizzare automaticamente i dati di mapping spaziale per risparmiare tempo all'utente. Quando non è possibile eseguire questa operazione in modo affidabile, le applicazioni devono invece consentire all'utente di fornire rapidamente all'applicazione le informazioni aggiuntive necessarie.

Per progettare l'esperienza di analisi ottimale, considerare quali delle possibilità seguenti sono applicabili all'applicazione:

* **Nessuna esperienza di analisi**
   * Un'applicazione può funzionare perfettamente senza alcuna esperienza di analisi guidata; apprenderà le superfici osservate nel corso del movimento naturale dell'utente.
   * Ad esempio, un'applicazione che consente all'utente di disegnare su superfici con una colorata di spray olografico richiede la conoscenza solo delle superfici attualmente visibili all'utente.
   * È possibile che l'ambiente sia già analizzato se è quello in cui l'utente ha già dedicato molto tempo all'uso del HoloLens.
   * Tenere tuttavia presente che la fotocamera usata dal mapping spaziale può vedere solo 3,1 m davanti all'utente, quindi il mapping spaziale non sarà in grado di conoscere superfici più distanti a meno che l'utente non le abbia osservate da una distanza più vicina in passato.
   * L'utente comprende quindi quali superfici sono state analizzate e l'applicazione deve fornire un feedback visivo a questo effetto, ad esempio il lancio di ombreggiature virtuali su superfici digitalizzate può aiutare l'utente a posizionare gli ologrammi su tali superfici.
   * In questo caso, i volumi di delimitazione dell'osservatore della superficie spaziale devono essere aggiornati a un sistema di [coordinate](coordinate-systems.md)spaziali bloccato dal corpo, in modo che seguano l'utente.

* **Trovare una posizione appropriata**
   * Un'applicazione può essere progettata per l'uso in una posizione con requisiti specifici.
   * Ad esempio, l'applicazione potrebbe richiedere un'area vuota intorno all'utente in modo che possa esercitarsi in modo sicuro con kung-fu olografico.
   * Le applicazioni devono comunicare all'utente in anticipo eventuali requisiti specifici e consolidarli con un feedback visivo chiaro.
   * In questo esempio, l'applicazione deve visualizzare l'estensione dell'area vuota richiesta ed evidenziare visivamente la presenza di oggetti indesiderati all'interno di questa zona.
   * In questo caso, i volumi di delimitazione dell'osservatore della superficie spaziale devono usare un sistema di [coordinate](coordinate-systems.md) spaziali bloccato a livello mondiale nella posizione scelta.

* **Trovare una configurazione appropriata delle superfici**
   * Un'applicazione può richiedere una configurazione specifica di superfici, ad esempio due grandi pareti piatte, opposte per creare una sala olografica di mirror.
   * In questi casi, l'applicazione dovrà analizzare le superfici fornite dal mapping spaziale per rilevare le superfici adatte e indirizzare l'utente verso di esse.
   * L'utente deve avere un'opzione di fallback se l'analisi della superficie dell'applicazione non è affidabile. Ad esempio, se l'applicazione identifica erroneamente una porta come una barriera piana, l'utente necessita di un modo semplice per correggere l'errore.

* **Analizzare parte dell'ambiente**
   * Un'applicazione potrebbe voler acquisire solo parte dell'ambiente, come indicato dall'utente.
   * Ad esempio, l'applicazione analizza parte di una stanza in modo che l'utente possa pubblicare un annuncio olografico classificato per i prodotti che vuole vendere.
   * In questo caso, l'applicazione deve acquisire i dati di mapping spaziale all'interno delle aree osservate dall'utente durante l'analisi.

* **Eseguire la scansione dell'intera stanza**
   * Un'applicazione può richiedere un'analisi di tutte le superfici nella stanza corrente, incluse quelle dietro l'utente.
   * Ad esempio, un gioco può mettere l'utente nel ruolo di Gulliver, sotto il controllo di centinaia di piccoli lilliputati che si avvicinano da tutte le direzioni.
   * In questi casi, l'applicazione dovrà determinare quante superfici nella stanza corrente sono già state analizzate e indirizzare lo sguardo dell'utente per riempire gap significativi.
   * La chiave di questo processo è fornire feedback visivo che indica chiaramente all'utente quali superfici non sono ancora state analizzate. L'applicazione potrebbe, ad esempio, usare [la lente](/windows/win32/direct3d9/fog-formulas) in base alla distanza per evidenziare visivamente le aree non coperte dalle superfici di mapping spaziale.

* **Creare uno snapshot iniziale dell'ambiente**
   * Un'applicazione potrebbe voler ignorare tutte le modifiche nell'ambiente dopo aver creato uno 'snapshot' iniziale.
   * Questo può essere appropriato per evitare l'interruzione dei dati creati dall'utente strettamente accoppiati allo stato iniziale dell'ambiente.
   * In questo caso, l'applicazione deve eseguire una copia dei dati di mapping spaziale nello stato iniziale al termine dell'analisi.
   * Le applicazioni devono continuare a ricevere aggiornamenti dei dati di mapping spaziale se gli ologrammi devono essere ancora occlusi correttamente dall'ambiente.
   * Gli aggiornamenti continui dei dati di mapping spaziale consentono anche di visualizzare eventuali modifiche apportate, chiarindo all'utente le differenze tra gli stati precedenti e presenti dell'ambiente.

* **Creare snapshot dell'ambiente avviati dall'utente**
   * Un'applicazione può voler rispondere alle modifiche ambientali solo se richiesto dall'utente.
   * Ad esempio, l'utente può creare più 'amici' 3D di un amico acquisendo le loro posizioni in momenti diversi.

* **Consentire all'utente di modificare l'ambiente**
   * Un'applicazione può essere progettata per rispondere in tempo reale alle modifiche apportate nell'ambiente dell'utente.
   * Ad esempio, l'utente che disegna un'incisa può attivare il "cambiamento della scena" per una riproduzione olografica che si svolge sull'altro lato.

* **Guida dell'utente per evitare errori nei dati di mapping spaziale**
   * Un'applicazione potrebbe voler fornire indicazioni all'utente durante l'analisi dell'ambiente.
   * Ciò consente all'utente di evitare determinati tipi di errori nei dati di [mapping](spatial-mapping.md#what-influences-spatial-mapping-quality)spaziale, ad esempio evitando finestre o mirror con luce solare.

Un dettaglio aggiuntivo da tenere presente è che l'intervallo dei dati di mapping spaziale non è illimitato. Anche se il mapping spaziale crea un database permanente di spazi di grandi dimensioni, rende disponibili i dati solo alle applicazioni in una "bolla" di dimensioni limitate intorno all'utente. Se si inizia all'inizio di un lungo periodo di tempo e ci si allontana abbastanza dall'inizio, alla fine le superfici spaziali all'inizio scompariranno. È possibile attenuare questo problema memorizzando nella cache tali superfici nell'applicazione dopo che sono scomparve dai dati di mapping spaziale disponibili.

## <a name="mesh-processing"></a>Elaborazione mesh

Può essere utile rilevare tipi comuni di errori nelle superfici e filtrare, rimuovere o modificare i dati di mapping spaziale in base alle esigenze.

Tenere presente che i dati di mapping spaziale sono destinati a essere il più possibile applicabili alle superfici reali, quindi qualsiasi elaborazione applicata rischia di spostare le superfici oltre la "verità".

Ecco alcuni esempi di diversi tipi di elaborazione mesh che possono risultare utili:

* **Riempimento di fori**
   * Se un piccolo oggetto costituito da un materiale scuro non riesce a eseguire la scansione, lascia un foro nella superficie circostante.
   * I fori influiscono sull'occlusione: gli ologrammi possono essere visti "attraverso" un foro in una superficie del mondo reale presumibilmente opaca.
   * I fori influiscono sui raycast: se si usano raycast per aiutare gli utenti a interagire con le superfici, potrebbe essere indesiderato che questi raggi passino attraverso i fori. Una mitigazione è l'uso di un bundle di più raycast che coprono un'area di dimensioni appropriate. In questo modo sarà possibile filtrare i risultati "outlier", in modo che anche se un raycast passa attraverso un piccolo foro, il risultato di aggregazione sarà comunque valido. Tuttavia, questo approccio comporta un costo di calcolo.
   * I fori influiscono sulle collisioni fisiche: un oggetto controllato dalla simulazione fisica può passare attraverso un foro nel piano e perdersi.
   * È possibile riempire in modo algoritmico tali fori nella mesh di superficie. Tuttavia, è necessario ottimizzare l'algoritmo in modo che i "buchi reali", ad esempio finestre e porte, non si riempia. Può essere difficile distinguere in modo affidabile i "fori reali" dai "fori immaginari", quindi è necessario sperimentare diverse euristiche, ad esempio "dimensioni" e "forma limite".

* **Rimozione dell'allucinazione**
   * Riflessi, luci colorate e oggetti in movimento possono lasciare piccole "allucinazioni" residue a metà aria.
   * Le allucinazioni influiscono sull'occlusione: le allucinazioni possono diventare visibili quando forme scuri si spostano davanti ad altri ologrammi e si occludono.
   * Le allucinazioni influiscono sui raycast: se si usano raycast per aiutare gli utenti a interagire con le superfici, questi raggi potrebbero avere un'allucinazione anziché la superficie dietro di essa. Come per i fori, una mitigazione è l'uso di molti raycast anziché di un singolo raycast, ma anche in questo caso questo avrà un costo di calcolo.
   * Le allucinazioni influiscono sulle collisioni fisiche: un oggetto controllato dalla simulazione fisica può rimanere bloccato contro un'allucinazione e non essere in grado di spostarsi attraverso un'area di spazio apparentemente chiara.
   * È possibile filtrare tali allucinazioni dalla mesh di superficie. Tuttavia, come per i fori, è necessario ottimizzare l'algoritmo in modo che oggetti di piccole dimensioni reali, ad esempio lampioni e punti di controllo delle porte, non vengono rimossi.

* **Definizione di movimenti uniformi**
   * Il mapping spaziale può restituire superfici che sembrano essere approssimative o "rumorose" rispetto alle controparti reali.
   * La smussatura influisce sulle collisioni fisiche: se il piano è ruvido, è possibile che una palla simulata fisicamente non si svolga senza problemi su di essa in linea retta.
   * La smussatura influisce sul rendering: se una superficie viene visualizzata direttamente, le normali della superficie approssimative possono influire sull'aspetto e interrompere un aspetto "pulito". È possibile attenuare questo problema usando l'illuminazione e le trame appropriate nello shader usato per eseguire il rendering della superficie.
   * È possibile uniformare la ruvidità in una mesh di superficie. Tuttavia, questo può allontanare la superficie dalla superficie reale corrispondente. Mantenere una corrispondenza accurata è importante per produrre occlusione accurata degli ologrammi e per consentire agli utenti di ottenere interazioni precise e prevedibili con le superfici olografiche.
   * Se è necessaria solo una modifica originale, può essere sufficiente uniformare le normali dei vertici senza modificare le posizioni dei vertici.

* **Ricerca di piani**
   * Esistono molte forme di analisi che un'applicazione potrebbe voler eseguire sulle superfici fornite dal mapping spaziale.
   * Un semplice esempio è la ricerca di piani. identificazione delle aree delimitate, principalmente planari delle superfici.
   * Le aree planari possono essere usate come superfici di lavoro olografiche, aree in cui il contenuto olografico può essere posizionato automaticamente dall'applicazione.
   * Le aree planari possono vincolare l'interfaccia utente per guidare gli utenti a interagire con le superfici più adatte alle proprie esigenze.
   * Le aree planari possono essere usate come nel mondo reale, per controparti olografiche di oggetti funzionali come schermi LCD, tabelle o lavagne.
   * Le aree planari possono definire aree di riproduzione, che formano la base dei livelli dei videogiochi.
   * Le aree planari possono aiutare gli agenti virtuali a spostarsi nel mondo reale, identificando le aree del piano su cui è probabile che passino persone reali.

## <a name="prototyping-and-debugging"></a>Prototipazione e debug

### <a name="useful-tools"></a>Strumenti utili

* [L HoloLens emulatore](../develop/platform-capabilities-and-apis/using-the-hololens-emulator.md) può essere usato per sviluppare applicazioni usando il mapping spaziale senza accesso a un HoloLens. Consente di simulare una sessione live in un HoloLens in un ambiente realistico, con tutti i dati normalmente utilizzati dall'applicazione, inclusi il movimento HoloLens, i sistemi di coordinate spaziali e le mesh di mapping spaziale. Può essere usato per fornire un input affidabile e ripetibile, che può essere utile per il debug dei problemi e la valutazione delle modifiche apportate al codice.
* Per riprodurre uno scenario, acquisire i dati di mapping spaziale in rete da un HoloLens live, quindi salvarli su disco e riutilizzarli nelle sessioni di debug successive.
* La [Windows 3D](../develop/platform-capabilities-and-apis/using-the-windows-device-portal.md#3d-view) del portale per dispositivi consente di visualizzare tutte le superfici spaziali attualmente disponibili tramite il sistema di mapping spaziale. In questo modo viene fornita una base di confronto per le superfici spaziali all'interno dell'applicazione. Ad esempio, è possibile capire facilmente se eventuali superfici spaziali sono mancanti o se vengono visualizzate nella posizione sbagliata.

### <a name="general-prototyping-guidance"></a>Linee guida generali per la prototipazione

* Poiché [gli](spatial-mapping.md#what-influences-spatial-mapping-quality) errori nei dati di mapping spaziale possono influire fortemente sull'esperienza dell'utente, è consigliabile testare l'applicazione in un'ampia gamma di ambienti.
* Non rimanere bloccati nell'consuetudine di eseguire sempre test nella stessa posizione, ad esempio in ufficio. Assicurarsi di eseguire test su diverse superfici di posizioni, forme, dimensioni e materiali diversi.
* Analogamente, anche se i dati sintetici o registrati possono essere utili per il debug, non fare affidamento troppo sui test case. Questo può ritardare la ricerca di problemi importanti che sarebbero stati individuati in precedenza da test più diversi.
* È buona idea eseguire test con utenti reali (e idealmente non raggiungibili), perché potrebbero non usare il HoloLens o l'applicazione esattamente come si fa. In realtà, può essere sorprendente quanto possono essere divergenti il comportamento, la conoscenza e i presupposti delle persone.

## <a name="troubleshooting"></a>Risoluzione dei problemi

* Per orientare correttamente le mesh di superficie, ogni GameObject deve essere attivo prima di essere inviato a SurfaceObserver per costruire la mesh. In caso contrario, le mesh verranno mostrate nello spazio, ma ruotate in angolazioni angolari.
* Il GameObject che esegue lo script che comunica con SurfaceObserver deve essere impostato sull'origine. In caso contrario, tutti i GameObject creati e inviati a SurfaceObserver per costruire le mesh avranno un offset uguale all'offset dell'oggetto gioco padre. In questo modo le mesh possono essere mostrate a diversi metri di distanza, il che rende difficile eseguire il debug di ciò che succede.

## <a name="see-also"></a>Vedi anche

* [Sistemi di coordinate](coordinate-systems.md)
* [Mapping spaziale in DirectX](../develop/native/spatial-mapping-in-directx.md)
* [Mapping spaziale in Unity](../develop/unity/spatial-mapping-in-unity.md)
* [Informazioni sulla scena](scene-understanding.md)
* [Visualizzazione della scansione dello spazio](room-scan-visualization.md)
* [Progettazione dell'audio spaziale](spatial-sound-design.md)
* [Case study - Guardare attraverso fori nella realtà](../out-of-scope/case-study-looking-through-holes-in-your-reality.md)
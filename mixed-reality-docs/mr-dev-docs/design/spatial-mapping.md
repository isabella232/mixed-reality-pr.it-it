---
title: Mapping spaziale
description: Il mapping spaziale fornisce una rappresentazione dettagliata delle superfici reali nell'ambiente intorno alla HoloLens.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: mapping spaziale, HoloLens, realtà mista, ricostruzione di superficie, mesh, auricolare realtà mista, auricolare di realtà mista, auricolare di realtà virtuale, HoloLens, MRTK, Toolkit di realtà mista, informazioni sulla scena, mesh globale, occlusione, fisica, navigazione, osservatore della superficie, rendering, elaborazione mesh
ms.openlocfilehash: 1c41706abc0a393e8530b38be83fed49ed3e20a6
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583270"
---
# <a name="spatial-mapping"></a>Mapping spaziale

Il mapping spaziale fornisce una rappresentazione dettagliata delle superfici reali nell'ambiente intorno alla HoloLens, consentendo agli sviluppatori di creare un'esperienza di realtà mista convincente. Unendo il mondo reale con il mondo virtuale, un'applicazione può sembrare reale. Le applicazioni possono anche essere allineate in modo più naturale con le aspettative degli utenti fornendo comportamenti e interazioni reali.

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

Il mapping spaziale consente di posizionare gli oggetti su superfici reali. In questo modo è possibile agganciare gli oggetti nel mondo dell'utente e sfruttare i vantaggi offerti dai suggerimenti per la profondità del mondo reale. Occlusione gli ologrammi in base ad altri ologrammi e oggetti reali consentono di convincere l'utente che questi ologrammi si trovano effettivamente nello spazio. Gli ologrammi che galleggiano nello spazio o che si avvicinano all'utente non si sentono come reali. Quando possibile, inserire gli elementi per comodità.

Visualizzare le superfici quando si posizionano o si spostano gli ologrammi (usare una griglia proiettata). Questo consente agli utenti di individuare il punto in cui possono posizionare i propri ologrammi e Mostra se la posizione in cui si sta tentando di collocare l'ologramma non è mappata. È possibile "Billboard Items" verso l'utente se terminano troppo di un angolo.

## <a name="conceptual-overview"></a>Panoramica dei concetti

![Superficie mesh che copre una stanza](images/SurfaceReconstruction.jpg)<br>
*Esempio di mesh di mapping spaziale che copre una stanza*

I due tipi di oggetti primari usati per il mapping spaziale sono "osservatore della superficie spaziale" e "superficie spaziale".

L'applicazione fornisce l'osservatore della superficie spaziale con uno o più volumi di delimitazione, per definire le aree di spazio in cui l'applicazione desidera ricevere i dati di mapping spaziali. Per ognuno di questi volumi, il mapping spaziale fornirà all'applicazione un set di superfici spaziali.

Questi volumi possono essere stazionari (in una posizione fissa basata sul mondo reale) oppure possono essere collegati a HoloLens (si spostano, ma non ruotano, con il HoloLens mentre si spostano nell'ambiente). Ogni superficie spaziale descrive le superfici reali in un piccolo volume di spazio, rappresentate come una mesh triangolare collegata a un [sistema di coordinate spaziali](coordinate-systems.md)con blocco globale.

Quando HoloLens raccoglie nuovi dati sull'ambiente e, quando si verificano modifiche all'ambiente, le superfici spaziali vengono visualizzate, scompaiono e modificate.

## <a name="spatial-mapping-vs-scene-understanding-worldmesh"></a>Confronto tra mapping spaziale e visione della scena WorldMesh

Per HoloLens 2, è possibile eseguire una query su una versione statica dei dati di mapping spaziale usando [scene Understanding SDK](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md) (impostazione EnableWorldMesh). Di seguito sono riportate le differenze tra due modalità di accesso ai dati di mapping spaziale:
* API di mapping spaziale:
   * Intervallo limitato: i dati di mapping spaziale disponibili per le applicazioni in una dimensione limitata memorizzata nella cache ' Bubble ' intorno all'utente.
   * Fornisce aggiornamenti a bassa latenza delle aree di rete modificate tramite eventi SurfacesChanged.
   * Livello variabile dei dettagli controllati da triangoli per ogni parametro del contatore cubo.
* Scenario di comprensione dell'SDK:
   * Intervallo illimitato: fornisce tutti i dati di mapping spaziale analizzati all'interno del raggio della query.
   * Fornisce uno snapshot statico dei dati di mapping spaziali. Per ottenere i dati di mapping spaziale aggiornati è necessario eseguire una nuova query per l'intera mesh.
   * Livello di dettaglio coerente controllato dall'impostazione RequestedMeshLevelOfDetail.

## <a name="what-influences-spatial-mapping-quality"></a>Che influenza la qualità del mapping spaziale?

Diversi fattori [, descritti in](/hololens/hololens-environment-considerations)dettaglio, possono influenzare la frequenza e la gravità di questi errori.  Tuttavia, è consigliabile progettare l'applicazione in modo che l'utente possa raggiungere gli obiettivi anche in presenza di errori nei dati di mapping spaziali.

## <a name="common-usage-scenarios"></a>Scenari di utilizzo comuni

![Illustrazioni degli scenari comuni di utilizzo del mapping spaziale: posizionamento, occlusione, fisica e navigazione](images/sm-concepts-1000px.png)

### <a name="placement"></a>Selezione host

Il mapping spaziale offre alle applicazioni l'opportunità di presentare forme di interazione naturale e familiare con l'utente; che cosa potrebbe essere più naturale rispetto a collocare il telefono sulla scrivania?

Vincolando la posizione degli ologrammi (o più in generale, qualsiasi selezione di posizioni spaziali) a cui poggiano le superfici, viene fornito un mapping naturale da 3D (punto nello spazio) a 2D (punto sulla superficie). In questo modo si riduce la quantità di informazioni che l'utente deve fornire all'applicazione e rende più veloce, semplice e preciso le interazioni dell'utente. Questo è vero perché' distance away ' non è un elemento che viene usato per la comunicazione fisica con altri utenti o computer. Quando puntiamo al dito, viene specificata una direzione, ma non una distanza.

Un avvertimento importante è che, quando un'applicazione deduce la distanza dalla direzione, ad esempio eseguendo un Raycast lungo la direzione dello sguardo dell'utente per trovare la superficie spaziale più vicina, questo deve produrre risultati che l'utente può prevedere in modo affidabile. In caso contrario, l'utente perderà il proprio senso di controllo e questa operazione può diventare rapidamente frustrante. Un metodo che consente di eseguire questa operazione consiste nell'eseguire più raycasts anziché uno solo. I risultati di aggregazione devono essere più uniformi e prevedibili, meno suscettibili a influenzare da risultati temporanei "outlier" (come può essere causato da raggi che passano attraverso piccoli buchi o colpendo piccoli bit di geometria di cui l'utente non è a conoscenza). L'aggregazione o l'uniformità può essere eseguita anche nel tempo; ad esempio, è possibile limitare la velocità massima a cui un ologramma può variare a distanza dall'utente. È anche possibile limitare la limitazione del valore minimo e massimo della distanza, in modo che l'ologramma spostato non entri improvvisamente nella distanza o venga arrestato di nuovo nel volto dell'utente.

Le applicazioni possono anche usare la forma e la direzione delle superfici per guidare la posizione degli ologrammi. Una poltrona olografica non dovrebbe penetrare tra le pareti e deve essere scaricata con il pavimento anche se è leggermente irregolare. Questo tipo di funzionalità si basa probabilmente sull'uso di collisioni di fisica anziché raycasts, tuttavia si verificheranno problemi simili. Se l'ologramma posizionato presenta molti poligoni di piccole dimensioni, come le gambe su una poltrona, potrebbe essere utile espandere la rappresentazione fisica di tali poligoni in modo più ampio e più semplice, in modo che siano più in grado di scorrere le superfici spaziali senza sbavare.

All'estremo, l'input dell'utente può essere completamente semplificato e può essere usato per eseguire la selezione automatica degli ologrammi. Ad esempio, l'applicazione potrebbe posizionare un interruttore di luce olografico in un punto qualsiasi sul muro per fare in modo che l'utente prema. La stessa avvertenza sulla prevedibilità si applica doppiamente. Se l'utente si aspetta di controllare la posizione degli ologrammi, ma l'applicazione non sempre posiziona gli ologrammi in cui si aspettano (se il Commuter viene visualizzato in un punto in cui l'utente non riesce a raggiungere), si tratta di un'esperienza frustrante. In realtà, è possibile che la selezione host automatica richieda la correzione dell'utente per un certo periodo di tempo, anziché richiedere che l'utente esegua sempre la selezione host. Poiché è *previsto* un posizionamento automatico corretto, la correzione manuale sembra un carico.

Si noti inoltre che la capacità di un'applicazione di utilizzare le superfici spaziali per la selezione host dipende molto dall' [esperienza di analisi](spatial-mapping.md#the-environment-scanning-experience)dell'applicazione. Se una superficie non è stata analizzata, non può essere usata per la selezione host. L'applicazione è in grado di rendere questa operazione chiara all'utente, in modo da consentire l'analisi di nuove superfici o la selezione di una nuova posizione.

Il feedback visivo all'utente è di importanza fondamentale durante la selezione host. L'utente deve essere in grado di individuare il punto in cui l'ologramma è basato sulla superficie più vicina con [effetti di base](spatial-mapping.md#visualization). Devono comprendere il motivo per cui lo spostamento del loro ologramma è vincolato, ad esempio a causa di collisioni con un'altra superficie vicina. Se non riescono a collocare un ologramma nella posizione corrente, il feedback visivo dovrebbe renderlo chiaro perché non. Ad esempio, se l'utente sta tentando di collocare un divano olografico a metà strada nella parete, le parti del divano che si trovano dietro la parete dovrebbero pulsare in un colore arrabbiato. O viceversa, se l'applicazione non riesce a trovare una superficie spaziale in una posizione in cui l'utente può visualizzare una superficie reale, l'applicazione dovrebbe renderla chiara. L'assenza ovvia di un effetto di base in quest'area può raggiungere questo scopo.

### <a name="occlusion"></a>Occlusione

Uno degli usi principali delle superfici di mapping spaziale è semplicemente occludere gli ologrammi. Questo semplice comportamento ha un notevole effetto sul realismo percepito degli ologrammi, contribuendo a creare un senso viscerale che si occupa effettivamente dello stesso spazio fisico dell'utente.

L'occlusione fornisce inoltre informazioni all'utente. Quando un ologramma sembra essere nascosto da una superficie reale, fornisce commenti visivi aggiuntivi relativi alla posizione spaziale di tale ologramma nel mondo. Viceversa, l'occlusione può anche *nascondere* le informazioni dall'utente. gli ologrammi occlusione dietro le pareti possono ridurre il disordine visivo in modo intuitivo. Per nascondere o rivelare un ologramma, l'utente deve semplicemente spostare l'intestazione.

L'occlusione può essere usata anche per le prime aspettative per un'interfaccia utente naturale basata su interazioni fisiche note. Se un ologramma è nascosto da una superficie, è perché la superficie è solida, quindi l'utente deve aspettarsi che l'ologramma entri in *conflitto* con tale superficie e non lo attraversi.

In alcuni casi, l'occlusione degli ologrammi è indesiderata. Se un utente deve interagire con un ologramma, deve visualizzarlo anche se è dietro una superficie reale. In questi casi, in genere è opportuno eseguire il rendering di un ologramma in modo diverso quando è nascosto (ad esempio, riducendo la luminosità). In questo modo, l'utente può individuare visivamente l'ologramma, ma saprà ancora che è dietro qualcosa.

### <a name="physics"></a>Fisica

L'uso della simulazione fisica è un altro modo in cui il mapping spaziale può essere usato per rafforzare la *presenza* di ologrammi nello spazio fisico dell'utente. Quando la palla di gomma olografica si sposta in modo realistico dalla mia scrivania, rimbalza sul pavimento e scompare sotto il divano, potrebbe essere difficile credere che non sia presente.

La simulazione fisica offre inoltre la possibilità per un'applicazione di usare interazioni naturali e familiari basate sulla fisica. Lo spostamento di un pezzo di mobili olografici intorno al pavimento sarà probabilmente più semplice per l'utente se il mobile risponde come se fosse scorrevole in tutto il pavimento con l'inerzia e l'attrito appropriati.

Per generare comportamenti fisici realistici, è probabile che sia necessario eseguire alcune operazioni di [elaborazione di mesh](spatial-mapping.md#mesh-processing) , ad esempio la compilazione di buchi, la rimozione di allucinazioni mobili e l'uniformità delle superfici ruvide.

Sarà inoltre necessario considerare il modo in cui l' [esperienza di analisi](spatial-mapping.md#the-environment-scanning-experience) dell'applicazione influisce sulla simulazione fisica. In primo luogo, le superfici mancanti non si scontrano con niente. cosa accade quando la palla di gomma si sposta verso il basso nel corridoio e al termine del mondo noto? In secondo luogo, è necessario decidere se continuare a rispondere alle modifiche nell'ambiente nel tempo. In alcuni casi, è opportuno rispondere il più rapidamente possibile; Supponiamo che l'utente usi porte e mobili come barriere mobili in difesa contro una tempesta di frecce romane in arrivo. In altri casi, tuttavia, potrebbe essere necessario ignorare i nuovi aggiornamenti; guidare le auto sportive olografiche in tutto il circuito può non essere così divertente se il cane decide di sedersi al centro della traccia.

### <a name="navigation"></a>Spostamento

Le applicazioni possono utilizzare i dati di mapping spaziale per concedere ai caratteri olografici (o agenti) la possibilità di esplorare il mondo reale nello stesso modo in cui una persona reale. Questo può contribuire a rafforzare la presenza di caratteri olografici limitando gli stessi allo stesso set di comportamenti naturali e noti di quelli dell'utente e dei relativi amici.

Le funzionalità di navigazione possono essere utili anche per gli utenti. Una volta che una mappa di navigazione è stata compilata in un'area specifica, potrebbe essere condivisa per fornire indicazioni olografiche per i nuovi utenti che non hanno familiarità con tale località. Questa mappa può essere progettata per semplificare il flusso del traffico pedonale o per evitare incidenti in posizioni pericolose come i siti di costruzione.

Le principali problemi tecnici che interessano l'implementazione della funzionalità di navigazione sono il rilevamento affidabile di superfici a scorrimento (gli utenti non sono in grado di esplorare le tabelle) e l'adattamento normale alle modifiche nell'ambiente (gli utenti non passano attraverso le porte chiuse). È possibile che la mesh richieda una certa [elaborazione](spatial-mapping.md#mesh-processing) prima che sia utilizzabile per la pianificazione del percorso e la navigazione da parte di un carattere virtuale. La smussatura della rete e la rimozione delle allucinazioni possono aiutare a evitare che i caratteri rimangano bloccati. È anche possibile semplificare notevolmente la rete per velocizzare i calcoli di spostamento e pianificazione dei percorsi dei caratteri. Questi problemi hanno ricevuto una grande attenzione nello sviluppo della tecnologia di gioco video ed è disponibile una vasta gamma di documenti di ricerca su questi argomenti.

La funzionalità NavMesh incorporata in Unity non può essere usata con superfici di mapping spaziale. Questo perché le superfici del mapping spaziale non sono note finché l'applicazione non viene avviata, ma i file di dati NavMesh devono essere generati in anticipo dalle risorse di origine. Si noti inoltre che il sistema di mapping spaziale non fornirà [informazioni sulle superfici lontani](spatial-mapping.md#the-environment-scanning-experience) dalla posizione corrente dell'utente. Quindi, l'applicazione deve ricordare che si tratta di una superficie per creare una mappa di un'area di grandi dimensioni.

### <a name="visualization"></a>Visualizzazione

Nella maggior parte dei casi è opportuno che le superfici spaziali siano invisibili; per ridurre al minimo il disordine visivo e lasciare che il mondo reale parli per se stesso. Tuttavia, a volte è utile visualizzare direttamente le superfici del mapping spaziale, nonostante le loro controparti reali siano visibili.

Ad esempio, quando l'utente tenta di posizionare un ologramma su una superficie (posizionando un cabinet olografico sulla parete), può essere utile per "macinare" l'ologramma proiettando un'ombreggiatura sulla superficie. Ciò offre all'utente un senso molto più chiaro della vicinanza fisica esatta tra l'ologramma e la superficie. Questo è anche un esempio della pratica più generale di "anteprima" visiva di una modifica prima che l'utente ne venga eseguito il commit.

Visualizzando le superfici, l'applicazione può condividere con l'utente la conoscenza dell'ambiente. Ad esempio, un gioco della lavagna olografica potrebbe visualizzare le superfici orizzontali identificate come ' Tables ', in modo che l'utente sappia dove devono interagire.

La visualizzazione delle superfici può essere un modo utile per visualizzare gli spazi adiacenti dell'utente nascosti dalla visualizzazione. Questo potrebbe fornire un modo per concedere all'utente l'accesso alla propria cucina (e a tutti gli ologrammi contenuti) dalla loro sala da vivere.

Le mesh di superficie fornite dal mapping spaziale potrebbero non essere particolarmente "pulite". È importante visualizzarli in modo appropriato. I calcoli di illuminazione tradizionali possono evidenziare gli errori nelle normalità della superficie in modo visivo, mentre le trame "pulite" proiettate sulla superficie possono contribuire a fornire un aspetto ordinato. È anche possibile eseguire l' [elaborazione mesh](spatial-mapping.md#mesh-processing) per migliorare le proprietà della mesh, prima che venga eseguito il rendering delle superfici.

> [!NOTE]
> HoloLens 2 implementa una nuova [scena che comprende il runtime](scene-understanding.md), che fornisce agli sviluppatori di realtà mista una rappresentazione dell'ambiente di alto livello strutturata progettata per semplificare l'implementazione di posizionamento, occlusione, fisica e navigazione.

## <a name="using-the-surface-observer"></a>Uso di Surface Observer

Il punto di partenza per il mapping spaziale è l'osservatore della superficie. Il flusso di programma è il seguente:
* Creare un oggetto Observer di superficie
   * Fornire uno o più volumi spaziali, per definire le aree di interesse in cui l'applicazione desidera ricevere i dati di mapping spaziali. Un volume spaziale è semplicemente una forma che definisce un'area di spazio, ad esempio una sfera o una casella.
   * Usare un volume spaziale con un sistema di coordinate spaziali con blocco globale per identificare un'area fissa del mondo fisico.
   * Usare un volume spaziale, aggiornare ogni frame con un sistema di coordinate spaziali con blocco del corpo per identificare un'area di spazio che si sposta (ma non ruota) con l'utente.
   * Questi volumi spaziali possono essere modificati in un secondo momento, in caso di modifica dello stato dell'applicazione o dell'utente.
* Usare il polling o la notifica per recuperare informazioni sulle superfici spaziali
   * È possibile eseguire il polling dell'osservatore della superficie per lo stato della superficie spaziale in qualsiasi momento. Al contrario, è possibile registrarsi per l'evento "Surfaces changed" dell'osservatore di superficie che invierà una notifica all'applicazione quando vengono modificate le superfici spaziali.
   * Per un volume spaziale dinamico, ad esempio la vista tronco o un volume con blocco del corpo, le applicazioni dovranno eseguire il polling delle modifiche per ogni frame impostando l'area di interesse e quindi ottenendo il set corrente di superfici spaziali.
   * Per un volume statico, ad esempio un cubo con blocco globale che copre un'unica stanza, è possibile che le applicazioni si registrino per l'evento "Surfaces changed" per ricevere una notifica in caso di modifica delle superfici spaziali all'interno di tale volume.
* Modifiche alle superfici del processo
   * Scorre il set di superfici spaziali fornito.
   * Classificare le superfici spaziali come aggiunte, modificate o rimosse.
   * Per ogni superficie spaziale aggiunta o modificata, se appropriato, inviare una richiesta asincrona per ricevere una mesh aggiornata che rappresenta lo stato corrente della superficie al livello di dettaglio desiderato.
* Elaborare la richiesta di mesh asincrona (altri dettagli nelle sezioni seguenti).

## <a name="mesh-caching"></a>Caching mesh

Le superfici spaziali sono rappresentate da mesh a triangolo denso. L'archiviazione, il rendering e l'elaborazione di tali mesh possono utilizzare risorse di calcolo e di archiviazione significative. Di conseguenza, ogni applicazione deve adottare uno schema di Caching mesh appropriato per le proprie esigenze, per ridurre al minimo le risorse usate per l'elaborazione e l'archiviazione di mesh. Questo schema deve determinare quali mesh tenere e quali rimuovere e quando aggiornare la mesh per ogni superficie spaziale.

Molte delle considerazioni illustrate in questo articolo indicheranno direttamente il modo in cui l'applicazione deve affrontare la memorizzazione nella cache. È necessario considerare il modo in cui l'utente si sposta nell'ambiente, quali sono le superfici necessarie, quando verranno osservate diverse superfici e quando le modifiche nell'ambiente devono essere acquisite.

Quando si interpreta l'evento "Surfaces changed" fornito da Surface Observer, la logica di base di caching della mesh è la seguente:
* Se l'applicazione rileva un ID di superficie spaziale che non ha visto prima, deve considerarlo come una nuova superficie spaziale.
* Se l'applicazione rileva una superficie spaziale con un ID noto ma con una nuova ora di aggiornamento, deve considerarla come una superficie spaziale aggiornata.
* Se l'applicazione non vede più una superficie spaziale con un ID noto, deve considerarla come una superficie spaziale rimossa.

Ogni applicazione deve quindi effettuare le scelte seguenti:
* Per le nuove superfici spaziali, è necessario richiedere la rete?
   * Generalmente la rete deve essere richiesta immediatamente per le nuove superfici spaziali, che possono fornire informazioni utili per l'utente.
   * Tuttavia, è necessario assegnare la priorità alle nuove superfici spaziali vicino e davanti all'utente e la loro mesh deve essere prima richiesta.
   * Se la nuova mesh non è necessaria, se ad esempio l'applicazione ha "bloccato" in modo permanente o temporaneo il relativo modello di ambiente, non dovrebbe essere richiesto.
* Per le superfici spaziali aggiornate, è necessario richiedere la rete?
   * È necessario assegnare la priorità a una superficie spaziale aggiornata vicina e davanti all'utente e la loro mesh deve essere richiesta per prima.
   * Potrebbe anche essere opportuno assegnare una priorità più alta alle nuove superfici rispetto alle superfici aggiornate, soprattutto durante l'esperienza di analisi.
   * Per limitare i costi di elaborazione, le applicazioni possono limitare la velocità con cui elaborano gli aggiornamenti delle superfici spaziali.
   * Potrebbe essere possibile dedurre che le modifiche apportate a una superficie spaziale sono minori, ad esempio se i limiti della superficie sono ridotti, nel qual caso l'aggiornamento potrebbe non essere sufficientemente importante da elaborare.
   * Gli aggiornamenti alle superfici spaziali al di fuori dell'area di interesse dell'utente possono essere ignorati completamente, anche se in questo caso potrebbe essere più efficiente modificare i volumi di delimitazione spaziali in uso da parte dell'osservatore della superficie.
* Per le superfici spaziali rimosse, il mesh dovrebbe essere scartato?
   * In genere, la mesh deve essere scartata immediatamente per le superfici spaziali rimosse, in modo che l'occlusione ologramma rimanga corretta.
   * Tuttavia, se l'applicazione ha motivo di ritenere che una superficie spaziale verrà nuovamente visualizzata a breve (in base alla progettazione dell'esperienza utente), potrebbe essere più efficiente evitare di scartare la mesh e ricrearla in un secondo momento.
   * Se l'applicazione sta creando un modello su larga scala dell'ambiente dell'utente, potrebbe non voler eliminare alcuna rete. Sarà comunque necessario limitare l'utilizzo delle risorse, probabilmente mediante lo spooling di mesh su disco quando le superfici spaziali scompaiono.
   * Alcuni eventi relativamente rari durante la generazione della superficie spaziale possono causare la sostituzione delle superfici spaziali con nuove superfici spaziali in un percorso simile ma con ID diversi. Quindi, le applicazioni che scelgono di non rimuovere una superficie rimossa dovrebbero prestare attenzione a non finire con più mesh di superfici spaziali altamente sovrapposte che coprono la stessa posizione.
* Il mesh deve essere scartato per qualsiasi altra superficie spaziale?
   * Anche quando esiste una superficie spaziale, se non è più utile per l'esperienza dell'utente, è consigliabile eliminarla. Se, ad esempio, l'applicazione sostituisce la stanza sull'altro lato di una porta con uno spazio virtuale alternativo, le superfici spaziali di tale spazio non sono più importanti.

Di seguito è riportato un esempio di strategia di Caching mesh, che usa l'isteresi spaziale e temporale:
* Si consideri un'applicazione che vuole usare un volume spaziale a forma di tronco di interesse che segue lo sguardo dell'utente nel modo in cui si aggirano.
* Una superficie spaziale può scomparire temporaneamente da questo volume semplicemente perché l'utente non è più in grado di uscire dalla superficie o da altri passaggi... solo per riprenderlo o ripeterlo più a breve. In questo caso, l'eliminazione e la ricreazione della mesh per questa superficie rappresentano molti processi ridondanti.
* Per ridurre il numero di modifiche elaborate, l'applicazione utilizza due osservatori di superficie spaziale, uno contenuto all'interno dell'altro. Il volume maggiore è sferico e segue l'utente "pigramente"; si sposta solo quando necessario per garantire che il centro sia entro 2,0 metri dall'utente.
* Le mesh di superficie spaziale nuove e aggiornate vengono sempre elaborate dall'osservatore della superficie interna più piccolo, ma le mesh vengono memorizzate nella cache fino a quando non vengono eliminate dal più ampio osservatore della superficie esterna. Ciò consente all'applicazione di evitare l'elaborazione di molte modifiche ridondanti a causa dello spostamento dell'utente locale.
* Poiché anche una superficie spaziale può scomparire temporaneamente a causa di una perdita di rilevamento, l'applicazione rinvia anche le aree spaziali rimosse durante la perdita di rilevamento.
* In generale, un'applicazione deve valutare il compromesso tra l'elaborazione degli aggiornamenti ridotta e un maggiore utilizzo della memoria per determinare la strategia di memorizzazione nella cache ideale.

## <a name="rendering"></a>Rendering

Esistono tre modi principali in cui i mesh di mapping spaziale tendono a essere usati per il rendering:
* Per la visualizzazione della superficie
   * Spesso è utile visualizzare direttamente le superfici spaziali. Ad esempio, il cast di ' Shadows ' da oggetti su superfici spaziali può fornire un utile feedback visivo all'utente mentre sta inserendo ologrammi sulle superfici.
   * Un aspetto da tenere presente è che le mesh spaziali sono diverse dal tipo di mesh che può essere creato da un artista 3D. La topologia triangolare non sarà' clean ' come topologia creata dall'uomo e la mesh soffrirà di [diversi errori](spatial-mapping.md#what-influences-spatial-mapping-quality).
   * Per creare una gradevole estetica visiva, è possibile eseguire alcune operazioni di [elaborazione della mesh](spatial-mapping.md#mesh-processing), ad esempio per riempire buchi o normali superfici uniformi. È anche possibile usare uno shader per proiettare le trame progettate dall'artista sulla mesh anziché visualizzare direttamente la topologia mesh e le normali.
* Per gli ologrammi occlusione dietro le superfici reali
   * È possibile eseguire il rendering delle superfici spaziali in un passaggio solo Depth, che influisce solo sul [buffer di profondità](/windows/win32/direct3d9/depth-buffers) e non influisce sulle destinazioni di rendering dei colori.
   * In questo modo, il buffer di profondità viene sottoposto a rendering degli ologrammi in occludere in seguito alle superfici spaziali. Una corretta occlusione degli ologrammi migliora il senso che gli ologrammi sono effettivamente presenti nello spazio fisico dell'utente.
   * Per abilitare il rendering con solo profondità, aggiornare lo stato di Blend per impostare [RenderTargetWriteMask](/windows/win32/api/d3d11_1/ns-d3d11_1-d3d11_render_target_blend_desc1) su zero per tutte le destinazioni di rendering dei colori.
* Per modificare l'aspetto degli ologrammi bloccati dalle superfici reali
   * In genere, la geometria sottoposta a rendering è nascosta quando è nascosta. Questa operazione viene eseguita impostando la funzione depth nello [stato depth-stencil](/windows/win32/api/d3d11/ns-d3d11-d3d11_depth_stencil_desc) su "minore o uguale a", che fa sì che la geometria sia visibile solo quando è **più vicina** alla fotocamera rispetto alla geometria sottoposta a rendering precedente.
   * Tuttavia, può essere utile tenere visibile una determinata geometria anche quando è bloccato e modificarne l'aspetto quando è bloccato come un modo per fornire un feedback visivo all'utente. Questo consente, ad esempio, all'applicazione di mostrare all'utente la posizione di un oggetto e di renderlo chiaro che si trova dietro una superficie reale.
   * Per ottenere questo risultato, eseguire il rendering della geometria una seconda volta con un shader diverso che crea l'aspetto "nascosto" desiderato. Prima di eseguire il rendering della geometria per la seconda volta, apportare due modifiche allo [stato di stencil Depth](/windows/win32/api/d3d11/ns-d3d11-d3d11_depth_stencil_desc). Per prima cosa, impostare la funzione depth su "maggiore o uguale a" in modo che la geometria sia visibile solo se è **più lontana** dalla fotocamera rispetto a tutte le geometrie precedentemente sottoposte a rendering. In secondo luogo, impostare DepthWriteMask su zero, in modo che il buffer di profondità non venga modificato (il buffer di profondità deve continuare a rappresentare la profondità della geometria **più vicina** alla fotocamera).

Le [prestazioni](../develop/platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md) sono un aspetto importante quando si esegue il rendering dei mesh di mapping spaziali. Di seguito sono riportate alcune tecniche di rendering specifiche per il rendering delle mesh di mapping spaziale:
* Regola densità triangolo
   * Quando si richiedono mesh di superficie spaziale dall'osservatore della superficie, richiedere la densità minima di mesh triangolari che è sufficiente per le proprie esigenze.
   * Potrebbe avere senso variare la densità del triangolo in base alla superficie, a seconda della distanza della superficie dall'utente e della relativa pertinenza all'esperienza utente.
   * La riduzione dei conteggi di triangolo ridurrà i costi di utilizzo della memoria e di elaborazione dei vertici sulla GPU, anche se non influirà sui costi di elaborazione dei pixel
* USA eliminazione tronco
   * L'eliminazione di tronco ignora gli oggetti Drawing che non possono essere visualizzati perché sono al di fuori dell'tronco di visualizzazione corrente. In questo modo si riducono i costi di elaborazione della CPU e della GPU.
   * Poiché l'abbassamento di livello viene eseguito in base a mesh e le superfici spaziali possono essere di grandi dimensioni, la suddivisione di ogni mesh della superficie spaziale in blocchi più piccoli può comportare un abbattimento più efficiente (in quanto viene eseguito il rendering di un numero inferiore di triangoli Offscreen). Tuttavia, esiste un compromesso; maggiore è il numero di mesh disponibili, maggiore è il numero di chiamate da creare, che possono aumentare i costi della CPU. In un caso estremo, i calcoli per l'eliminazione di tronco possono anche avere un costo della CPU misurabile.
* Modificare l'ordine di rendering
   * Le superfici spaziali tendono a essere di grandi dimensioni, perché rappresentano l'intero ambiente dell'utente che la circonda. I costi di elaborazione dei pixel sulla GPU possono essere elevati, soprattutto nei casi in cui è presente più di un livello di geometria visibile, incluse le superfici spaziali e altri ologrammi. In questo caso, il livello più vicino all'utente occlusione i livelli più lontani, quindi qualsiasi tempo GPU dedicato al rendering di questi livelli più distanti viene sprecato.
   * Per ridurre questo lavoro ridondante sulla GPU, è possibile eseguire il rendering di superfici opache in ordine da primo a indietro (più vicine prima, più distanti le ultime). Per "opaque" si intende la superficie per la quale DepthWriteMask è impostato su uno nello [stato depth-stencil](/windows/win32/api/d3d11/ns-d3d11-d3d11_depth_stencil_desc). Quando viene eseguito il rendering delle superfici più vicine, il buffer di profondità verrà preimpostato in modo che le superfici più remote vengano ignorate in modo efficiente dal processore pixel sulla GPU.

## <a name="mesh-processing"></a>Elaborazione mesh

Un'applicazione potrebbe voler eseguire [varie operazioni](spatial-mapping.md#mesh-processing) sulle mesh della superficie spaziale in base alle proprie esigenze. I dati relativi a indici e vertici forniti con ogni mesh di superficie spaziale utilizzano lo stesso layout familiare dei [vertex buffer e degli indici](/windows/win32/direct3d9/rendering-from-vertex-and-index-buffers) utilizzati per il rendering di mesh triangolari in tutte le moderne API di rendering. Tuttavia, un fatto fondamentale da tenere presente è che i triangoli di mapping spaziale hanno un **ordine di avvolgimento in senso antiorario**. Ogni triangolo è rappresentato da tre indici di vertice nel buffer di indice della mesh e questi indici identificano i vertici del triangolo in un ordine **orario** , quando il triangolo viene visualizzato dal lato **anteriore** . Il lato anteriore (o esterno) delle mesh della superficie spaziale corrisponde a quello previsto per il lato anteriore (visibile) delle superfici reali.

Le applicazioni devono solo semplificare la rete se la densità del triangolo più grossolana fornita dall'osservatore di superficie è ancora insufficiente. questo lavoro è dispendioso dal punto di vista del calcolo ed è già eseguito dal runtime per generare i vari livelli di dettaglio forniti.

Poiché ogni osservatore di superficie può fornire più aree spaziali non connesse, alcune applicazioni potrebbero voler ritagliare le mesh della superficie spaziale tra loro, quindi riunirle. In generale, il passaggio di ritaglio è necessario, in quanto le mesh della superficie spaziale sono spesso sovrapposte leggermente.

## <a name="raycasting-and-collision"></a>Raycasting e collisione

Affinché un'API fisica, ad esempio [Havok](https://www.havok.com/), fornisca un'applicazione con funzionalità di Raycasting e collisione per le superfici spaziali, l'applicazione deve fornire mesh di superficie spaziale all'API di fisica. Le mesh usate per la fisica hanno spesso le proprietà seguenti:
* Contengono solo un numero ridotto di triangoli. Le operazioni di fisica sono più complesse dal punto di vista delle operazioni di rendering.
* Si tratta di un "Water-Tight". Le superfici destinate a essere solide non devono contenere piccoli buchi; anche i buchi troppo piccoli per essere visibili possono causare problemi.
* Sono convertite in gusci convessi. Le gusci convessi hanno pochi poligoni e sono privi di buchi e sono molto più efficienti dal punto di vista del calcolo rispetto a mesh triangolari grezzi.

Quando si esegue raycasts in base alle superfici spaziali, tenere presente che queste superfici sono spesso complesse e ingombranti di dettagli, come la propria scrivania. Ciò significa che un singolo Raycast è spesso insufficiente per fornire informazioni sufficienti sulla forma della superficie e sulla forma dello spazio vuoto vicino. È in genere consigliabile eseguire molti raycasts all'interno di una piccola area e usare i risultati di aggregazione per derivare una conoscenza più affidabile della superficie. Ad esempio, l'uso della media di 10 raycasts per guidare la posizione degli ologrammi su una superficie produrrà un risultato molto più semplice e meno "nervosa" che usa solo un singolo raycast.

Tuttavia, tenere presente che ogni Raycast può avere un elevato costo computazionale. A seconda dello scenario di utilizzo, è consigliabile comportare il costo di calcolo di raycasts aggiuntivi (eseguita ogni frame) rispetto al costo computazionale dell' [elaborazione della rete](spatial-mapping.md#mesh-processing) per smussare e rimuovere i buchi nelle superfici spaziali (eseguite quando vengono aggiornate le mesh spaziali).

## <a name="the-environment-scanning-experience"></a>Esperienza di analisi dell'ambiente

Ogni applicazione che usa il mapping spaziale deve considerare la possibilità di fornire un'esperienza di analisi. processo attraverso il quale l'applicazione guida l'utente per l'analisi delle superfici necessarie per il corretto funzionamento dell'applicazione.

![Esempio di analisi](images/sr-mixedworld-140429-8pm-00068-1000px.png)<br>
*Esempio di analisi*

La natura di questa esperienza di analisi può variare significativamente a seconda delle esigenze di ogni applicazione, ma due principi principali dovrebbero guidare la progettazione.

In primo luogo, **una comunicazione chiara con l'utente rappresenta il problema principale**. L'utente deve sempre tenere presente se i requisiti dell'applicazione vengono soddisfatti. Quando non vengono soddisfatte, dovrebbe essere immediatamente chiaro all'utente perché questo è così e dovrebbe essere portato rapidamente a intraprendere l'azione appropriata.

In secondo luogo, **le applicazioni devono provare a trovare un equilibrio tra efficienza e affidabilità**. Quando è possibile eseguire questa operazione in modo **affidabile**, le applicazioni devono analizzare automaticamente i dati del mapping spaziale per salvare l'ora utente. Quando non è possibile eseguire questa operazione in modo affidabile, le applicazioni devono invece consentire all'utente di fornire rapidamente all'applicazione le informazioni aggiuntive necessarie.

Per semplificare la progettazione dell'esperienza di analisi corretta, considerare quali delle seguenti possibilità sono applicabili all'applicazione:

* **Nessuna esperienza di analisi**
   * Un'applicazione può funzionare perfettamente senza alcuna esperienza di analisi guidata; verranno fornite informazioni sulle superfici osservate nel corso del movimento naturale dell'utente.
   * Ad esempio, un'applicazione che consente all'utente di disegnare sulle superfici con la vernice spray olografica richiede solo le informazioni sulle superfici attualmente visibili all'utente.
   * L'ambiente potrebbe essere già stato analizzato se ne è uno in cui l'utente ha già impiegato molto tempo con HoloLens.
   * Tenere presente, tuttavia, che la fotocamera usata dal mapping spaziale può visualizzare solo 3,1 m davanti all'utente, quindi il mapping spaziale non saprà altre superfici distanti, a meno che l'utente non abbia osservato da una distanza più vicina in passato.
   * Quindi, l'utente riconosce quali superfici sono state analizzate, l'applicazione deve fornire un feedback visivo a questo effetto, ad esempio il cast di ombre virtuali su superfici analizzate può aiutare l'utente a collocare gli ologrammi su tali superfici.
   * Per questo caso, i volumi di delimitazione dell'osservatore della superficie spaziale devono aggiornare ogni frame a un sistema di [coordinate spaziali](coordinate-systems.md)con blocco del corpo, in modo che seguano l'utente.

* **Trovare un percorso adatto**
   * Un'applicazione può essere progettata per essere utilizzata in una posizione con requisiti specifici.
   * Ad esempio, l'applicazione può richiedere un'area vuota per l'utente in modo da poter provare a utilizzare in modo sicuro il kung-fu olografico.
   * Le applicazioni devono comunicare i requisiti specifici per l'utente in primo piano e rinforzarli con un chiaro feedback visivo.
   * In questo esempio, l'applicazione deve visualizzare l'ambito dell'area vuota richiesta e evidenziare visivamente la presenza di oggetti indesiderati all'interno di questa zona.
   * Per questo caso, i volumi di delimitazione dell'osservatore della superficie spaziale devono usare un [sistema di coordinate spaziali](coordinate-systems.md) con blocco globale nella posizione scelta.

* **Trovare una configurazione adatta delle superfici**
   * È possibile che un'applicazione richieda una configurazione specifica delle superfici, ad esempio due pareti grandi, piatte e contrapposte, per creare una sala olografica di mirror.
   * In questi casi, l'applicazione dovrà analizzare le superfici fornite dal mapping spaziale per rilevare le superfici appropriate e indirizzare l'utente verso loro.
   * Se l'analisi della superficie dell'applicazione non è affidabile, l'utente deve disporre di un'opzione di fallback. Se, ad esempio, l'applicazione identifica erroneamente un portale come un muro Flat, l'utente deve disporre di un modo semplice per correggere l'errore.

* **Analizza parte dell'ambiente**
   * Un'applicazione può voler acquisire solo parte dell'ambiente, come indicato dall'utente.
   * Ad esempio, l'applicazione analizza parte di una stanza, in modo che l'utente possa pubblicare un annuncio olografico per la mobilia che desidera vendere.
   * In questo caso, l'applicazione deve acquisire i dati di mapping spaziali all'interno delle aree osservate dall'utente durante la relativa analisi.

* **Analizza l'intera stanza**
   * Un'applicazione può richiedere un'analisi di tutte le superfici nella stanza corrente, incluse quelle dietro l'utente.
   * Ad esempio, un gioco può mettere l'utente nel ruolo di Gulliver, in assiege da centinaia di piccoli Lillipuziani che si avvicinano da tutte le direzioni.
   * In questi casi, l'applicazione dovrà determinare il numero di superfici presenti nella stanza corrente è già stata analizzata e indicare allo sguardo dell'utente di colmare gap significative.
   * La chiave per questo processo è fornire feedback visivo che rende chiaro all'utente quali superfici non sono ancora state analizzate. L'applicazione potrebbe, ad esempio, usare la [nebbia basata sulla distanza](/windows/win32/direct3d9/fog-formulas) per evidenziare visivamente le aree non coperte dalle superfici di mapping spaziale.

* **Eseguire uno snapshot iniziale dell'ambiente**
   * Un'applicazione potrebbe voler ignorare tutte le modifiche apportate all'ambiente dopo aver eseguito uno snapshot iniziale.
   * Questa operazione può essere utile per evitare l'intralcio di dati creati dall'utente strettamente collegati allo stato iniziale dell'ambiente.
   * In questo caso, l'applicazione deve creare una copia dei dati di mapping spaziale nello stato iniziale al termine dell'analisi.
   * Le applicazioni devono continuare a ricevere gli aggiornamenti dei dati di mapping spaziale se gli ologrammi rimangono ancora correttamente bloccati dall'ambiente.
   * Gli aggiornamenti continui dei dati di mapping spaziali consentono inoltre di visualizzare le modifiche apportate, chiarendo all'utente le differenze tra gli stati precedenti e quelli presenti nell'ambiente.

* **Eseguire snapshot dell'ambiente avviati dall'utente**
   * Un'applicazione può solo voler rispondere alle modifiche ambientali quando richiesto dall'utente.
   * Ad esempio, l'utente può creare più "statue" 3D di un amico acquisendo le loro pose in momenti diversi.

* **Consenti all'utente di modificare l'ambiente**
   * Un'applicazione può essere progettata in modo da rispondere in tempo reale a tutte le modifiche apportate nell'ambiente dell'utente.
   * Ad esempio, l'utente che disegna una tenda potrebbe attivare la "modifica della scena" per una riproduzione olografica che avviene sull'altro lato.

* **Guida dell'utente per evitare errori nei dati di mapping spaziale**
   * Un'applicazione potrebbe voler fornire indicazioni all'utente durante l'analisi dell'ambiente.
   * Ciò consente all'utente di evitare determinati tipi di [errori nei dati di mapping spaziali](spatial-mapping.md#what-influences-spatial-mapping-quality), ad esempio rimanendo fuori da finestre o mirror luminosi.

Un ulteriore dettaglio da tenere presente è che il ' intervallo ' dei dati di mapping spaziali non è illimitato. Sebbene il mapping spaziale crei un database permanente di spazi di grandi dimensioni, rende solo i dati disponibili per le applicazioni in una "bolla" di dimensioni limitate per l'utente. Se si inizia dall'inizio di un lungo corridoio e si procede abbastanza lontano dall'inizio, infine le superfici spaziali all'inizio scompariranno. Per attenuare questo problema, è possibile memorizzare nella cache tali superfici nell'applicazione dopo che sono scomparse dai dati di mapping spaziali disponibili.

## <a name="mesh-processing"></a>Elaborazione mesh

Potrebbe essere utile rilevare tipi comuni di errori nelle superfici e filtrare, rimuovere o modificare i dati del mapping spaziale in base alle esigenze.

Tenere presente che i dati di mapping spaziali sono destinati a essere il più fedele possibile a superfici reali, quindi qualsiasi elaborazione applicata rischia di spostare ulteriormente le superfici dalla "verità".

Di seguito sono riportati alcuni esempi di diversi tipi di elaborazione di mesh che possono risultare utili:

* **Riempimento foro**
   * Se non è possibile eseguire l'analisi di un oggetto di piccole dimensioni con un materiale scuro, questo lascerà un foro nell'area circostante.
   * I buchi influiscono sull'occlusione: gli ologrammi possono essere visualizzati in un foro in una superficie reale opaca.
   * I buchi influiscono su raycasts: se si usa raycasts per aiutare gli utenti a interagire con le superfici, potrebbe essere indesiderato che questi raggi attraversino buchi. Una mitigazione consiste nell'usare un bundle di più raycasts che coprono un'area opportunamente dimensionata. Ciò consentirà di filtrare i risultati "outlier", in modo che anche se un Raycast passa attraverso un piccolo foro, il risultato dell'aggregazione sarà ancora valido. Tuttavia, questo approccio comporta un costo computazionale.
   * I buchi influiscono sui conflitti di fisica: un oggetto controllato dalla simulazione fisica può essere trascinato in una buca al pavimento e perso.
   * È possibile algoritmicamente colmare tali buchi nella mesh della superficie. Tuttavia, sarà necessario ottimizzare l'algoritmo in modo che non vengano compilati ' buchi reali ', ad esempio Windows e porte. Può essere difficile distinguere in modo affidabile ' buchi reali ' da' buchi immaginari ', quindi è necessario provare con euristiche diverse, ad esempio ' dimensioni ' è forma limite '.

* **Rimozione delle allucinazioni**
   * I riflessi, le luci luminose e gli oggetti mobili possono lasciare piccole "allucinazioni" fluttuanti a mezz'aria.
   * Le allucinazioni influiscono sull'occlusione: le allucinazioni possono essere visibili come forme scure che si avvicinano a e occlusione altri ologrammi.
   * Le allucinazioni influiscono su raycasts: se si usa raycasts per aiutare gli utenti a interagire con le superfici, questi raggi potrebbero raggiungere una allucinazione invece della superficie sottostante. Come per i buchi, una mitigazione consiste nell'usare molti raycasts invece di un singolo Raycast, ma anche in questo caso il costo di calcolo sarà elevato.
   * Le allucinazioni influiscono sui conflitti di fisica: un oggetto controllato dalla simulazione fisica può rimanere bloccato contro un'allucinazione e non essere in grado di spostarsi in un'area di spazio apparentemente chiara.
   * È possibile filtrare tali allucinazioni dalla mesh della superficie. Tuttavia, come per i buchi, sarà necessario ottimizzare l'algoritmo in modo da evitare la rimozione di oggetti di piccole dimensioni, ad esempio luci e maniglie degli sportelli.

* **Definizione di movimenti uniformi**
   * Il mapping spaziale può restituire superfici che sembrano essere ruvide o ' noisy ' rispetto alle controparti reali.
   * La fluidità influiscono sui conflitti di fisica: se il piano è ruvido, una palla da golf simulata fisicamente potrebbe non essere posizionata senza intoppi in una linea retta.
   * La fluidità influisce sul rendering: se una superficie viene visualizzata direttamente, le normali superfici ruvide possono influire sul proprio aspetto e interferire con l'aspetto "Pulisci". È possibile mitigare questo problema usando l'illuminazione e le trame appropriate nello shader usato per il rendering della superficie.
   * È possibile smussare l'rugosità in una mesh di superficie. Questa operazione può tuttavia comportare la disattivazione della superficie dalla superficie reale corrispondente. La gestione di una corrispondenza di chiusura è importante per produrre un'occlusione olografica accurata e consentire agli utenti di ottenere interazioni precise e prevedibili con le superfici olografiche.
   * Se è necessaria solo una modifica cosmetica, può essere sufficiente per smussare i normali vertici senza modificare le posizioni del vertice.

* **Ricerca del piano**
   * Esistono diverse forme di analisi che un'applicazione può voler eseguire sulle superfici fornite dal mapping spaziale.
   * Un semplice esempio è' ricerca del piano '; identificazione delle aree delimitate, principalmente planari di superfici.
   * Le aree planari possono essere usate come superfici di lavoro olografiche, aree in cui il contenuto olografico può essere inserito automaticamente dall'applicazione.
   * Le aree planari possono vincolare l'interfaccia utente per guidare gli utenti a interagire con le superfici più adatte alle proprie esigenze.
   * Le aree planari possono essere usate come nel mondo reale, per le controparti olografiche in oggetti funzionali quali schermi LCD, tabelle o lavagne.
   * Le aree piane possono definire aree di riproduzione, che costituiscono la base dei livelli di gioco video.
   * Le aree planari possono aiutare gli agenti virtuali a esplorare il mondo reale, identificando le aree del piano su cui è probabile che le persone reali possano procedere.

## <a name="prototyping-and-debugging"></a>Prototipi e debug

### <a name="useful-tools"></a>Strumenti utili

* L' [emulatore di HoloLens](../develop/platform-capabilities-and-apis/using-the-hololens-emulator.md) può essere usato per sviluppare applicazioni usando il mapping spaziale senza accedere a un HoloLens fisico. Consente di simulare una sessione in tempo reale in un HoloLens in un ambiente realistico, con tutti i dati normalmente utilizzati dall'applicazione, tra cui HoloLens Motion, sistemi di coordinate spaziali e mesh di mapping spaziale. Questo può essere usato per fornire un input affidabile e ripetibile, che può essere utile per il debug dei problemi e la valutazione delle modifiche apportate al codice.
* Per riprodurre uno scenario, acquisire i dati di mapping spaziali sulla rete da un HoloLens attivo, quindi salvarli su disco e riutilizzarli in sessioni di debug successive.
* La [visualizzazione 3D del portale per dispositivi Windows](../develop/platform-capabilities-and-apis/using-the-windows-device-portal.md#3d-view) consente di visualizzare tutte le superfici spaziali attualmente disponibili tramite il sistema di mapping spaziale. In questo modo viene fornita una base di confronto per le superfici spaziali all'interno dell'applicazione. ad esempio, è possibile stabilire facilmente se eventuali superfici spaziali risultano mancanti o visualizzate nella posizione sbagliata.

### <a name="general-prototyping-guidance"></a>Indicazioni generali sulla prototipazione

* Poiché gli [errori](spatial-mapping.md#what-influences-spatial-mapping-quality) nei dati di mapping spaziali possono influire fortemente sull'esperienza dell'utente, è consigliabile testare l'applicazione in un'ampia gamma di ambienti.
* Non rimanere intrappolato nell'abitudine di testare sempre nella stessa posizione, ad esempio nella propria scrivania. Assicurarsi di eseguire il test su varie superfici di posizioni, forme, dimensioni e materiali differenti.
* Analogamente, mentre i dati sintetici o registrati possono essere utili per il debug, non dipendono troppo dagli stessi test case. Questo può ritardare la ricerca di problemi importanti che potrebbero essere rilevati in precedenza da più test.
* È consigliabile eseguire i test con utenti reali (e idealmente non allenati), perché non possono usare il HoloLens o l'applicazione esattamente come si fa. In realtà, può sorprendere il comportamento, la conoscenza e le ipotesi delle persone divergenti.

## <a name="troubleshooting"></a>Risoluzione dei problemi

* Affinché le mesh della superficie siano orientate correttamente, ogni GameObject deve essere attivo prima di essere inviato al SurfaceObserver per costruire la mesh. In caso contrario, le maglie vengono visualizzate nello spazio, ma ruotate a angoli strani.
* Il GameObject che esegue lo script che comunica con il SurfaceObserver deve essere impostato sull'origine. In caso contrario, tutte le GameObject create e inviate al SurfaceObserver per la costruzione delle mesh avranno un offset uguale all'offset dell'oggetto del gioco padre. In questo modo, le mesh vengono visualizzate a diversi metri, il che rende difficile il debug di ciò che accade.

## <a name="see-also"></a>Vedere anche

* [Sistemi di coordinate](coordinate-systems.md)
* [Mapping spaziale in DirectX](../develop/native/spatial-mapping-in-directx.md)
* [Mapping spaziale in Unity](../develop/unity/spatial-mapping-in-unity.md)
* [Comprensione della scena](scene-understanding.md)
* [Visualizzazione della scansione dello spazio](room-scan-visualization.md)
* [Progettazione dell'audio spaziale](spatial-sound-design.md)
* [Case study - Guardare attraverso fori nella realtà](../out-of-scope/case-study-looking-through-holes-in-your-reality.md)
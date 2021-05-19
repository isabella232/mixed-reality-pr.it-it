---
title: Designing Holograms
description: Informazioni sulla realtà mista tramite la nuova applicazione Microsoft Designing Holograms.
author: hferrone
ms.author: daescu
ms.date: 11/24/2020
ms.topic: article
keywords: MRTK, Mixed Reality Toolkit, ologrammi, progettazione di ologrammi, apprendimento, app di esempio, visore per realtà mista, visore per realtà virtuale, che cos'è la realtà virtuale
ms.openlocfilehash: 6e37c3f1ba98f202addb9c323632bca8bffae3b6
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143635"
---
# <a name="the-making-of-designing-holograms"></a>Creazione di ologrammi di progettazione

> [!NOTE]
> Consentire una piccola finestra di caricamento per tenere conto di tutte le GIF e i video incorporati in questa pagina.

Imparare a progettare per la realtà mista può essere difficile perché il supporto non sempre si traduce bene in processi di progettazione 2D. In Microsoft è stata creata un'app gratuita per il HoloLens 2 per apprendere in prima persona i concetti fondamentali di UX Design per la realtà mista. L'approccio unico dell'app Designing Holograms si insedia in comportamenti, suggerimenti e consigli di realtà mista per creare app HoloLens accattivanti e straordinarie. Scaricare l'app gratuitamente dal Microsoft Store e apprendere dal team di progettazione di Realtà mista di Microsoft.

> [!div class="nextstepaction"]
> [Scaricare l'app Designing Holograms](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)

<br>

![GIF animata della scena di rilevamento della testa nella sala demo di Designing Hologram](images/designing-holograms/demo-room.gif)

*Progettazione della demo room di Hologram (nota anche come casa delle bambole)*

## <a name="designing-for-mixed-reality"></a>Progettazione per la realtà mista

Come molti di voi, ho usato per progettare app per dispositivi mobili. Proveniente da un mondo di progettazione 2D, il passaggio completo al calcolo spaziale, dove tutto è ora nel mondo, è stato un cambiamento significativo. In realtà mista, le app non sono più limitate a uno schermo 2D; In realtà, sono quasi gratuiti, inseriti nel mondo reale e interagiscono con oggetti reali.

Per me, connettere esperienze 3D a processi di progettazione 2D convenzionali è l'aspetto più complesso dello sviluppo di realtà mista. Nelle conversazioni con i clienti si udivano elementi come "So quali funzionalità includere e come ottenerle. È codice, è possibile seguire la documentazione e le esercitazioni, ma l'esperienza utente? Molte funzionalità, opzioni di input diverse, scenari diversi e ambienti fisici sono molto difficili".

![Immagine del workshop HoloLens 2 design a San Francisco Immagine del ](images/designing-holograms/workshop.jpeg)
 *workshop HoloLens 2 design di San Francisco*

## <a name="an-opportunity-to-teach"></a>Un'opportunità per insegnare

All'inizio non era ovvio, ma è stata presentata un'ottima opportunità per usare la realtà mista come mezzo per insegnarla.

La progettazione di ologrammi è un'esperienza visiva che illustra i concetti e le raccomandazioni di progettazione della realtà mista. Si tratta solo dell'utente e di un insegnante virtuale che illustra i concetti di progettazione della realtà mista. Tutto è da una prospettiva di terza persona con l'esperienza che si trova nel proprio spazio.

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Designing-Holograms-app-trailer/player]

*Video sulla progettazione di trailer di ologrammi*

## <a name="exploring-the-doll-house"></a>Esplorazione della casa del caseino

La casa della casa è l'ambiente virtuale che viene utilizzato in tutta l'app. L'ambiente è una stanza in miniatura di 80 x 60 x 40 cm che contiene gli elementi di base che la maggior parte delle stanze ha in comune, ad esempio pareti, lampioni, mobili, un tavolo e una TV. La casa della casa è il principale elemento dell'esperienza dell'app, quindi è necessario assicurarsi che funzioni bene in qualsiasi ambiente. Può essere un piccolo spazio dimostrativo per la visualizzazione di tutti i tipi di concetti di realtà mista.

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Dollhouse-adjustment-behavior-in-the-Designing-Holograms-app/player]
*Video del comportamento di regolazione diHouse*

### <a name="11-vs-110-prototypes"></a>Prototipi 1:1 e 1:10

Il presupposto iniziale era che le dimostrazioni 1:1 sarebbero state straordinarie, quasi come guardare un insegnante reale. L'utente dovrebbe vedere tutto ciò che vede il docente su scala reale. Tuttavia, ci siamo subito resi conto che ci sarebbero stati alcuni problemi:

- La maggior parte degli sviluppatori eseguirà le app in uffici o stanze più piccole rispetto alla demo, quindi non è adatta.
- Gli schermi sono additivi, ovvero l'intero ambiente virtuale verrà sovrapposto alla stanza di un utente. Questo può creare confusione con due tabelle, forse doppi divano e pareti che non sono allineate.
- E il peggiore di tutti gli ambienti virtuali è fortemente vincolato da un campo di visualizzazione.

Quando è stata provata una scala minima di 1:10, il risultato era una vista accattivante di una stanza realistica. È possibile vedere tutto ciò che succedeva da qualsiasi angolo nello stesso momento. La cosa più sorprendente è che la maggior parte dei tester l'ha trovata molto più immersiva per vedere una versione ridotta, quindi non è mai tornati alla scala 1:1. Si è quindi deciso di scartare effettivamente la versione 1:1 ed evitare il lavoro aggiuntivo necessario per adattare l'interfaccia utente e altri aspetti dell'app.

![Campo di visualizzazione con scala 1:1 Campo di visualizzazione ](images/designing-holograms/1-1-scale.png)
 *con scala 1:1*

![Campo di visualizzazione con scala 1:10 Campo di visualizzazione ](images/designing-holograms/1-10-scale.png)
 *con scala 1:10*

## <a name="using-mixed-reality-capture"></a>Uso di Acquisizione realtà mista

Una delle funzionalità più caratteristiche di questa app è l'uso di Acquisizione realtà mista per insegnare e illustrare i concetti di progettazione della realtà mista.

Microsoft ha una Acquisizione realtà mista studio a San Francisco. Microsoft licenzerà questa tecnologia anche in altri studi, tra cui Avatar Dimension a Washington D.C., Metastage a Los Angeles, Dimension Studio a Londra, SK Telecom a Seattle e Volucap a Sydney. Altre informazioni sui nostri Acquisizione realtà mista [Studio sono disponibili qui.](https://www.microsoft.com/mixed-reality/capture-studios)

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Raw-capture-footage-for-the-Designing-Holograms-app/player]
*Raw cameras of Daniel Escudero from one of the 106 cameras in the Acquisizione realtà mista Studio in San Francisco.*

Il processo di acquisizione genera una mesh con fotogrammi chiave, normali e trama, che può essere recapitata come file OBJ/PNG per un'ulteriore post-produzione o pronta per la riproduzione come file MP4 compresso H.264. Questi file possono essere importati in progetti Unity, Unreal, Native e WebXR. I file possono essere eseguiti in Windows, iOS, Mac, Android, Magic Leap e Playstation VR.

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Mixed-Reality-Capture-footage-for-the-Designing-Holograms-app/player]
*Capture Player fornito per analizzare i file mp4 contenenti video con mesh incorporate e audio.*

## <a name="manipulating-captures-and-virtual-objects"></a>Manipolazione di acquisizioni e oggetti virtuali

Le acquisizioni di realtà mista producono rappresentazioni virtuali di persone o animali, ma a volte potrebbero essere necessari per interagire con altri oggetti virtuali. I due esempi seguenti illustrano diversi modi in cui le scene sono stati manipolate per ottenere questo effetto.

### <a name="head-gaze-adjustment"></a>Regolazione dello sguardo della testa

La regolazione dell'headgaze consente di spostare la testa di una persona acquisita in fase di esecuzione, ovvero si potrebbe avere un viso di acquisizione verso un utente. In questo caso, è stato usato per visualizzare il campo di visualizzazione e il campo di interesse. Quello che si vede di seguito è un oggetto di gioco in movimento che funge da destinazione per lo sguardo rivolto verso la testa. Quando si sposta la destinazione da un lato all'altro, l'intestazione dell'acquisizione segue.

Questo trucco è stato usato per assicurarsi che l'acquisizione inattiva si faccia sempre verso ologrammi posizionati in diverse parti della casa delle bambole. 

![La testa dell'acquisizione viene spostata in fase di esecuzione in seguito a un gameobject di destinazione in Unity](images/designing-holograms/head-adjustment.gif)

*La testa dell'acquisizione viene spostata in fase di esecuzione in seguito a un gameobject di destinazione in Unity.*

### <a name="syncing-animated-objects"></a>Sincronizzazione di oggetti animati

Il secondo, animava gli oggetti per la sincronizzazione con lo spostamento di un'acquisizione. In parti diverse dell'app sono stati importati OBJ sequenziali di un'acquisizione specifica ogni cinque fotogrammi. Gli OBJ sono stati quindi animati nella scena per assicurarsi che corrispondano al fotogramma corrispondente dell'acquisizione. Si tratta di un processo noioso di animazione e keyframing, ma il risultato è ottimo. È ora possibile visualizzare un Acquisizione realtà mista che interagisce con oggetti non acquisiti.

![Animazione sincronizzata tra un Acquisizione realtà mista e il pannello dell'interfaccia utente](images/designing-holograms/synced-objects.gif)

*Animazione sincronizzata tra un Acquisizione realtà mista e il pannello dell'interfaccia utente*

### <a name="ui-creative-process"></a>Processo di creazione dell'interfaccia utente

Quando è stata avviata la progettazione dell'interfaccia utente, si è voluto mostrare alcuni dei magic e delle possibilità che gli ologrammi hanno da offrire. La semplice visualizzazione di finestre e caselle di testo 2D statiche non è una scelta giusta nel mondo 3D. Molte delle possibilità disponibili non vengono mostrate, quindi fin dall'inizio si è deciso di allontanarsi da questa possibilità e di usare completamente lo spazio 3D olografico.

All'inizio è stato aggiunto uno spessore ai pannelli, alle icone e alle informazioni di testo. Tuttavia, come utente, quello che viene visualizzato è una casella di testo. Caselle di testo con immagini, ma non sono presenti. Abbiamo fatto di più usando gli shader di Mixed Reality Toolkit (MRTK). Gli shader MRTK sono diventati uno strumento potente ed è stato fatto uso delle funzionalità degli stencil per aggiungere profondità negativa ai pannelli. Ciò significa che invece di aggiungere elementi davanti a una casella di testo, le icone vengono ora visualizzate dietro un pannello trasparente. Quello che si vede ora come utente è qualcosa che non è più possibile replicare nel mondo reale ed è qui che inizia a verificarsi il magic olografico. Inoltre, come utente che non mi piace leggere, posso fare molto già nel mondo fisico.

Ovviamente le icone funzionano molto meglio del testo semplice. Per fornire indicazioni ancora più potenti, ho quindi iniziato a creare un set di oggetti animati e avatar, ognuno dei quali racconta una piccola storia su ciò che viene fatto nel rispettivo scenario e su come viene usato.

![GIF animata di un sistema di menu olografico interattivo](images/designing-holograms/creative-process.gif)

## <a name="core-concepts"></a>Concetti di base

**Tracciamento della testa e tracciamento oculare**

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Head-Tracking-and-Eye-Tracking-Chapter/player]

**Tracciamento delle mani**

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Hand-Tracking-Chapter/player]

**Consapevolezza spaziale**

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Spatial-Awareness-Chapter/player]

**Frame olografico**

![GIF animata di un utente che guarda intorno al cascinato con la cornice olografica evidenziata](images/designing-holograms/FOVandFOI.gif)

**Sistemi di coordinate**

![GIF animata di un utente che guarda intorno alla caserma con i sistemi di coordinate evidenziati](images/designing-holograms/CoordinateSystems.gif)

**Tracciamento oculare**

![GIF animata di un utente che guarda gli ologrammi stazionari con il raggio dello sguardo fisso evidenziato](images/designing-holograms/EyeTracking.gif)

**Visualizzazione dell'analisi della stanza e mapping spaziale**

![GIF animata di tutte le superfici all'interno dell'cascina da mappare](images/designing-holograms/SpatialMapping.gif)

**Informazioni sulle scene**

![GIF animata di oggetti nel caseino riconosciuto](images/designing-holograms/SceneUnderstanding.gif)

**Puntare ed eseguire il commit con i raggi della mano**

![GIF animata di un utente che alza la mano con un raggio della mano evidenziato](images/designing-holograms/HandRays.gif)

## <a name="try-it-out-moments"></a>Momenti di "Prova"

La progettazione di ologrammi insegna concetti di realtà mista, ma consente anche di provarli in camera. Dopo alcune di queste spiegazioni, ci si sospende e si esce dalla casa delle bambole e si entra in un momento interattivo. Ecco alcuni esempi di questi momenti interattivi:

![GIF animata del frame di rilevamento della mano che mostra quando vengono rilevate le mani e quando entrano nel campo di visualizzazione](images/designing-holograms/try-out-1.gif)

*Frame di rilevamento della mano che mostra quando vengono rilevate le mani e quando entrano nel campo di visualizzazione.*

![GIF animata dell'interazione con i cristallo in collisione tramite l'interazione da lontano](images/designing-holograms/try-out-2.gif)

*Interazione con i cristallo in collisione attraverso l'interazione da lontano*

![GIF animata dell'esplorazione delle interazioni near affordances](images/designing-holograms/try-out-3.gif)

*Esplorazione degli affordance di interazione vicina*

## <a name="about-the-team"></a>Informazioni sul team

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Daniel Escudero" width="60" height="60" src="images/designing-holograms/daniel-escudero.jpeg"></td>
<td style="border-style: none"><b>Daniel Escudero</b><br><i>Lead Technical Designer</i><br>Dan è creative director per la progettazione di ologrammi e attualmente lavora come Responsabile della progettazione per la Mixed Reality Academy di Microsoft a San Francisco e in precedenza è stato designer in uno dei Mixed Reality Studios di Microsoft a Londra.</td>
</tr>
</table>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Martin Wettig" width="60" height="60" src="images/designing-holograms/martin-wettig.jpeg"></td>
<td style="border-style: none"><b>Martin Wettig</b><br><i>Senior 3D Artist</i><br>Martin è a capo di 3D Art and UI Design on Designing Holograms e in precedenza è stato Senior 3D Artist in uno dei Mixed Reality Studios di Microsoft a Berlino.</td>
</tr>
</table>

Un grazie enorme al team di progettazione di realtà mista per la condivisione di così tante conoscenze e agli straordinari colleghi di [Object Theory](https://objecttheory.com/) per essere membri essenziali del team in ogni passaggio del progetto. Grazie a tutti per il tuo straordinario speaker, per la tua passione e la tua grande attenzione per la progettazione.

> [!div class="nextstepaction"]
> [Scaricare l'app Designing Holograms (Progettazione di ologrammi)](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)
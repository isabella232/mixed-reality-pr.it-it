---
title: Progettazione di ologrammi
description: Scopri la realtà mista tramite la nuova applicazione per la progettazione di ologrammi di Microsoft.
author: hferrone
ms.author: daescu
ms.date: 11/24/2020
ms.topic: article
keywords: MRTK, Toolkit per realtà mista, ologrammi, progettazione di ologrammi, apprendimento, app di esempio, auricolare realtà mista, auricolare della realtà virtuale, informazioni sulla realtà virtuale
ms.openlocfilehash: 243b6f28da7b074b3ff6d48794d525ac08281fa7
ms.sourcegitcommit: 09522ab15a9008ca4d022f9e37fcc98f6eaf6093
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/30/2020
ms.locfileid: "96355436"
---
# <a name="the-making-of-designing-holograms"></a>Creazione della progettazione di ologrammi

> [!NOTE]
> Per tenere conto di tutte le gif interessanti e dei video incorporati in questa pagina, è necessario attendere una piccola finestra di caricamento.

L'apprendimento della progettazione per la realtà mista può essere difficile, soprattutto in merito alla modalità di visualizzazione del supporto, che non sempre si traduce correttamente nei processi di progettazione 2D. In Microsoft è stata creata un'app gratuita che è possibile scaricare per HoloLens 2, che consente di apprendere le nozioni di base sulla progettazione di UX realtà mista sperimentando l'it in prima persona. L'approccio esclusivo dell'app di progettazione degli ologrammi si immerge in comportamenti di realtà misti, suggerimenti e consigli per la creazione di app HoloLens accattivanti e straordinarie. Scarica gratuitamente l'app dal Microsoft Store e impara dal team Microsoft Mixed Reality Design.

> [!div class="nextstepaction"]
> [Scaricare l'app per la progettazione di ologrammi](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)

<br>

![GIF animata della scena di rilevamento Head nella stanza demo dell'ologramma di progettazione](images/designing-holograms/demo-room.gif)

*Progettazione dello spazio dimostrativo dell'ologramma (noto anche come casa di bambola)*

## <a name="designing-for-mixed-reality"></a>Progettazione per realtà mista

Come molti di voi, ho usato per progettare app per dispositivi mobili. Dal punto di vista di un ambiente di progettazione 2D, il passaggio all'intero ambiente di calcolo spaziale, in cui tutto è ora in tutto il mondo, è stato un cambiamento significativo. In realtà mista, le app non sono più confinate in una schermata 2D; Infatti, sono quasi gratuite, si trovano nel mondo reale e interagiscono con gli oggetti reali.

Per me, la connessione di esperienze 3D ai processi di progettazione 2D convenzionali è l'aspetto più complesso dello sviluppo di realtà miste. Nelle conversazioni con i clienti, mi sento di sapere quali sono le funzionalità da includere e come renderle operativi. Si tratta di codice, posso seguire la documentazione e le esercitazioni, ma l'esperienza utente? Così tante funzionalità, diverse opzioni di input, diversi scenari e ambienti fisici, è molto difficile.

![Immagine del workshop di progettazione HoloLens 2 nell'immagine di San Francisco del ](images/designing-holograms/workshop.jpeg)
 *workshop di progettazione HoloLens 2 a San Francisco*

## <a name="an-opportunity-to-teach"></a>Opportunità di insegnare

Inizialmente non era ovvio, ma era stata presentata un'opportunità eccellente per usare la realtà mista come supporto per insegnarlo.

La progettazione di ologrammi è un'esperienza visiva che illustra i concetti e le raccomandazioni di progettazione della realtà mista. Si tratta solo di un insegnante virtuale che illustra concetti di progettazione di realtà mista. Tutto dipende dal punto di vista di una terza persona con l'esperienza nello spazio.

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Designing-Holograms-app-trailer/player]

*Video sulla progettazione degli ologrammi trailer*

## <a name="exploring-the-doll-house"></a>Esplorazione della casa di bambola

Il Doll House è l'ambiente virtuale usato nell'app, una stanza in miniatura 80 x 60 x 40 cm che contiene gli elementi di base che la maggior parte delle stanze hanno in comune, ad esempio muri, lampade, mobilia, una tabella e una TV. La casa Doll è il protagonista principale dell'esperienza dell'app, quindi è necessario assicurarsi che funzioni perfettamente in qualsiasi ambiente. Considerarlo come una piccola stanza demo per visualizzare tutti i tipi di concetti di realtà mista.

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Dollhouse-adjustment-behavior-in-the-Designing-Holograms-app/player]
*Video del comportamento di regolazione della Dollhouse*

### <a name="11-vs-110-prototypes"></a>1:1 prototipi di Visual Studio 1:10

Il presupposto iniziale era che le dimostrazioni di 1:1 sarebbero state sorprendenti, quasi come la ricerca di un insegnante di vita reale. L'utente vedrebbe tutti gli elementi che il docente vede a una reale scalabilità. Tuttavia, si è capito immediatamente che ci sarebbero alcuni problemi:

- La maggior parte degli sviluppatori eseguirà le proprie app in uffici o in ambienti di dimensioni inferiori rispetto a quelle dimostrative.
- Gli schermi sono additivi, ovvero l'intero ambiente virtuale verrà sovrapposto alla stanza di un utente. Questo può creare confusione con due tabelle, forse doppi divani e muri che non si allineano.
- E peggiori di tutto un ambiente virtuale limitato da un campo di visualizzazione.

Quando è stata tentata una scala mini 1:10, il risultato è una splendida vista di uccelli in una sala realistica in cui è possibile visualizzare tutto ciò che era in corso da qualsiasi angolo e così via. Ciò che era più sorprendente è che la maggior parte dei tester ritenesse molto più immersiva per visualizzare una versione ridotta, quindi non si è mai attivata la scala 1:1. Quindi abbiamo deciso di rimuovere la versione 1:1 ed evitare il lavoro aggiuntivo necessario per adattare l'interfaccia utente e altri aspetti dell'app.

![Campo di visualizzazione con il ](images/designing-holograms/1-1-scale.png)
 *campo di visualizzazione scalabile 1:1 con scala 1:1*

![Campo di visualizzazione con il ](images/designing-holograms/1-10-scale.png)
 *campo di visualizzazione scalabile 1:10 con scala 1:10*

## <a name="using-mixed-reality-capture"></a>Uso dell'acquisizione di realtà mista

Una delle funzionalità più caratteristiche di questa app è l'uso dell'acquisizione di realtà mista per insegnare e dimostrare concetti di progettazione della realtà mista.

Microsoft dispone di uno studio di acquisizione di realtà mista a San Francisco. Microsoft concede anche questa tecnologia ad altri studio, tra cui la dimensione avatar a Washington D.C., metastage a Los Angeles, Dimension Studios a Londra, SK Telecom a Seoul e Volucap a Berlino. Qui è possibile trovare altre informazioni sugli [studi di acquisizione di realtà miste](https://www.microsoft.com/mixed-reality/capture-studios).

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Raw-capture-footage-for-the-Designing-Holograms-app/player]
*Metraggio non elaborato di Daniel Escudero da una delle fotocamere 106 in Mixed Reality Capture Studio a San Francisco.*

Il processo di acquisizione genera una mesh, normali e una trama con fotogrammi chiave, che possono essere recapitati come file OBJ/PNG per un ulteriore post-produzione o pronti per la riproduzione come file MP4 compresso H. 264. Questi file possono essere importati in Unity, Unreal, native e WebXR ed eseguiti in Windows, iOS, Mac, Android, Magic LEAP e PlayStation VR.

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Mixed-Reality-Capture-footage-for-the-Designing-Holograms-app/player]
*Il lettore di acquisizione fornito per analizzare mp4s che contengono video con reti audio e mesh incorporate.*

## <a name="manipulating-captures-and-virtual-objects"></a>Manipolazione di acquisizioni e oggetti virtuali

Le acquisizioni di realtà miste producono rappresentazioni virtuali di persone o animali, ma in alcuni casi potrebbe essere necessario usare tali caratteri per interagire con altri oggetti virtuali. I due esempi seguenti illustrano i diversi modi in cui abbiamo modificato le scene per ottenere questo effetto.

### <a name="head-gaze-adjustment"></a>Regolazione dello sguardo Head

La regolazione Headgaze consente di spostare la testa di una persona acquisita in fase di esecuzione, vale a dire che è possibile avere un volto di acquisizione verso un utente. In questo caso, è stato usato per visualizzare il campo di visualizzazione e il campo di interesse. Di seguito è riportato un GameObject che funge da destinazione per lo sguardo a capo. Quando si sposta la destinazione da Side a Side, l'intestazione dell'acquisizione segue.

Questo espediente è stato usato per assicurarsi che l'acquisizione inattiva sia sempre rivolta agli ologrammi posizionati in parti diverse della casa di bambola. 

![L'intestazione di acquisizione viene spostata in fase di esecuzione dopo un GameObject di destinazione in Unity](images/designing-holograms/head-adjustment.gif)

*L'intestazione dell'acquisizione viene spostata in fase di esecuzione dopo un GameObject di destinazione in Unity.*

### <a name="syncing-animated-objects"></a>Sincronizzazione di oggetti animati

Il secondo è stato l'animazione degli oggetti da sincronizzare con lo spostamento di un'acquisizione. In diverse parti dell'app sono stati importati obj sequenziali di un'acquisizione specifica ogni cinque frame. Il obj è stato quindi animato nella scena per verificare che corrispondano al frame corrispondente dell'acquisizione. Si tratta di un processo noioso di animazione e di fotogrammi, ma il risultato è notevole, ora è possibile vedere un'acquisizione di realtà mista che interagisce con oggetti non acquisiti.

![Animazione sincronizzata tra un'acquisizione di realtà mista e un pannello dell'interfaccia utente](images/designing-holograms/synced-objects.gif)

*Animazione sincronizzata tra un'acquisizione di realtà mista e un pannello dell'interfaccia utente*

### <a name="ui-creative-process"></a>Processo creativo dell'interfaccia utente

Quando abbiamo iniziato a ideando la progettazione dell'interfaccia utente, oltre alle informazioni di trasporto, vorremmo anche mostrare parte della magia e delle possibilità offerte dagli ologrammi. La semplice visualizzazione di finestre 2D statiche e caselle di testo non si trova nel mondo 3D e non mostra molte delle possibilità a disposizione, quindi fin dall'inizio abbiamo deciso di uscire da questo e sfruttare completamente lo spazio 3D olografico.

Inizialmente, abbiamo iniziato ad aggiungere uno spessore ai pannelli e alle icone oltre alle informazioni di testo. Tuttavia, come un utente, viene visualizzata una casella di testo. Caselle di testo con immagini, ma non sono presenti. Siamo andati oltre usando gli shader MRTK (Mixed Reality Toolkit). Gli shader MRTK sono diventati uno strumento potente ed è stato fatto uso delle funzionalità degli stencil, alcuni possono conoscerlo come effetto del portale, per aggiungere una profondità negativa ai pannelli. Ciò significa invece di aggiungere elementi davanti a una casella di testo, le icone vengono ora visualizzate dietro un pannello trasparente. Ora, come un utente è qualcosa che non riesco più a replicare nel mondo reale e questo è il punto in cui la magia olografica è iniziata. Inoltre, un utente che non mi piace leggere, lo faccio molto già nel mondo fisico.

Ovviamente le icone funzionano in modo molto migliore rispetto al testo semplice, quindi, per fornire una guida ancora più potente, ho iniziato a creare un set di oggetti animati e avatar, ognuno dei quali racconta una piccola storia di ciò che viene eseguito nel rispettivo scenario e del modo in cui viene usato.

![GIF animata di un sistema di menu interattivo olografico](images/designing-holograms/creative-process.gif)

## <a name="try-it-out-moments"></a>Minuti di prova

La progettazione di ologrammi insegna concetti di realtà mista, ma consente anche di provarli nella propria stanza. Una volta apportate alcune di queste spiegazioni, viene sospesa la casa di bambola e in un momento interattivo. Di seguito sono riportati alcuni esempi di questi momenti interattivi:

![GIF animata del frame di rilevamento mano che mostra quando vengono rilevate mani e quando entrano nel campo della visualizzazione](images/designing-holograms/try-out-1.gif)

*Frame di rilevamento mano che indica quando vengono rilevate le mani e quando entrano nel campo della visualizzazione.*

![GIF animata di interazione con i cristalli in collisione attraverso un'interazione molto più lunga](images/designing-holograms/try-out-2.gif)

*Interazione con i cristalli in collisione attraverso un'interazione molto più lunga*

![GIF animata di esplorazione near Interaction affordances](images/designing-holograms/try-out-3.gif)

*Esplorazione di near Interaction affordances*

## <a name="about-the-team"></a>Informazioni sul team

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Daniel Escudero" width="60" height="60" src="images/designing-holograms/daniel-escudero.jpeg"></td>
<td style="border-style: none"><b>Daniel Escudero</b><br><i>Progettista tecnico lead</i><br>Dan è il direttore creativo sulla progettazione degli ologrammi e attualmente funziona come responsabile della progettazione per la realtà mista di Microsoft a San Francisco ed è stato in precedenza un progettista di uno degli studi di realtà mista di Microsoft a Londra.</td>
</tr>
</table>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Martin Wettig" width="60" height="60" src="images/designing-holograms/martin-wettig.jpeg"></td>
<td style="border-style: none"><b>Martin Wettig</b><br><i>Artista 3D Senior</i><br>Martin conduce grafica 3D e progettazione dell'interfaccia utente sulla progettazione di ologrammi ed era in precedenza un artista 3D senior in uno degli studi di realtà mista di Microsoft a Berlino.</td>
</tr>
</table>

Un grande ringraziamento al team di progettazione della realtà mista per la condivisione di una conoscenza di questo genere e naturalmente per le persone straordinarie che hanno preso parte alla [teoria degli oggetti](https://objecttheory.com/) che è diventato un compagno di squadra essenziale in ogni singolo passaggio di questo progetto. Grazie per il talento straordinario, per la passione e per gli occhi eccezionali per la progettazione.

> [!div class="nextstepaction"]
> [Scaricare l'app per la progettazione di ologrammi](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)
---
title: Case study - Rappresentazione degli esseri umani nella realtà mista
description: Che tipo di opportunità emergono quando non è possibile creare solo elementi straordinari, ma usare le acquisizioni più realistiche di ambienti, oggetti e persone nella realtà mista?
author: mavitazk
ms.author: jemccull
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, esseri umani, avatar, acquisizione di realtà mista, video volumetrico
ms.openlocfilehash: db21b6b02ce76403c2c59e37384c1c1602d8a63e003a8b5b6601c5daf7b9c2a7
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115228528"
---
# <a name="case-study---representing-humans-in-mixed-reality"></a>Case study - Rappresentazione degli esseri umani nella realtà mista

James Turrell progetta con luce. L'approfondimento del suo lavoro offusca il senso di profondità e messa a fuoco. Le pareti sembrano vicine e infinite, la luminosità lascia il modo alle ombreggiature. Percezioni sconosciute progettate bilanciando con attenzione il colore e la diffusione della luce. [Turrell descrive queste sentimenti come](https://www.sculpture.org/documents/scmag02/nov02/turrell/turrell.shtml) *"sentimenti con gli* occhi", un modo per estendere la comprensione della realtà. Mondi fantastici, come quello che Turrell immagina, sono strumenti potenti per sfruttare i sensi, non diversamente dagli ambienti immersivi della realtà mista di oggi.

![Wide Out - James Turrell (1998)](../develop/platform-capabilities-and-apis/images/wide-out-james-turrell.jpg)

## <a name="how-do-you-represent-complex-real-world-environments-in-mixed-reality"></a>Come si rappresentano ambienti reali complessi nella realtà mista?

Rappresentare il lavoro di Turrell in un'esperienza immersiva rappresenta una sfida interessante. Illuminazione, scalabilità e audio spaziale offrono opportunità per rappresentare il suo lavoro. Anche se l'ambiente geometrico dell'esposizione richiede una modellazione 3D relativamente semplice, è secondario all'attenzione dell'artista: l'impatto della luce sui sensi.

Il minimalismo crudo e minimalismo di Turrell è il segno distintivo del suo lavoro, ma cosa succede se si vuole rappresentare una mostra con materiali più complessi nella realtà mista?

![Bang - Ai Weiwei (2013)](../develop/platform-capabilities-and-apis/images/bang-ai-weiwie.jpg)

Nel 2013, l'artista Ai Weiwei ha presentato un'opera d'arte aggrovigliante che include 886 sgabelli di antiquariato alla Mostra di Architettura di Venezia. [](https://www.designboom.com/art/ai-weiwei-bang-installation-at-venice-art-biennale-2013/) Ogni sgabello in legno proveniva da un'era in cui la tradizione cinese era molto apprezzata, in cui questi sgabelli sarebbero stati trasmersi tra generazioni. Gli sgabelli stessi, ovvero le complessità del legna, la precisione dei pezzi, il loro posizionamento attento, sono fondamentali per il commento di Ai sulla cultura moderna.

Gli sgabelli antiquariato recapitare il messaggio dell'artista attraverso la loro autenticità. La rappresentazione realistica è fondamentale per l'esperienza, creando una sfida tecnica: scolpire ognuno degli sgabelli 886 manualmente sarebbe estremamente esaustivo e costoso. Quanto tempo sarebbe necessario per modellare e posizionare? Come si mantiene l'autenticità del materiale? Ricreare questi oggetti da zero diventa, in molti modi, un'interpretazione dell'opera d'arte stessa. Come si può mantenere la finalità dell'artista?

## <a name="methods-of-capturing-mixed-reality-assets"></a>Metodi di acquisizione di asset di realtà mista

L'alternativa alla creazione di qualcosa da zero è l'acquisizione della cosa reale. Grazie a un set sempre più avanti di metodi di acquisizione, è possibile sviluppare rappresentazioni autentiche di ognuno dei tipi di asset principali presenti nella realtà mista (ambienti, oggetti e persone).

Le ampie categorie vanno dai video 2D ben affermati alle forme più recenti di video volumetrico. Nel caso della mostra di Ai Weiwei, la scansione (spesso indicata dalla tecnica fondamentale, la fotogrammetria) può essere utilizzata durante la creazione della mostra, eseguendo la scansione di ognuno degli sgabelli stessi. L'acquisizione di foto e video a 360° è un altro metodo per virtualizzare l'esperienza utilizzando una fotocamera omnidirezionale di alta qualità posizionata in tutta la mostra. Con queste tecniche si inizia a comprendere il senso della scala, idealmente con un numero di dettagli sufficiente per vedere l'eccellenza di ogni pezzo. Tutto questo mentre esiste in una forma digitale che consente nuovi punti di vista e prospettive non possibili in realtà.

![Video da 2D a volumetrico](../develop/platform-capabilities-and-apis/images/2d-to-volumetric-video.png)

Che tipo di opportunità emergono quando non è possibile creare solo elementi straordinari, ma usare le acquisizioni più realistiche di ambienti, oggetti e persone nella realtà mista? L'esplorazione della sovrapposizione tra questi metodi consente di illuminare la posizione del supporto.

Per ambienti e oggetti, il software di creazione di immagini a 360° si sta evolvendo per includere elementi di fotogrammetria. Isolando le informazioni di profondità dalle scene, i video avanzati a 360° aiutano ad attenuare la sensazione di avere la testa bloccata in una specie di fishbowl quando ci si guarda intorno a una scena virtuale.

Per gli utenti stanno emergendo nuovi metodi che combinano ed estendono l'acquisizione del movimento e la scansione: l'acquisizione del movimento è stata alla base per portare il movimento umano dettagliato agli effetti visivi e ai caratteri cinematografici, mentre la scansione è avanzata per acquisire oggetti visivi umani dettagliati come visi e mani. Con i progressi nella tecnologia di rendering, un nuovo metodo denominato video volumetrico crea queste tecniche, combinando informazioni visive e di profondità, per creare la prossima generazione di acquisizioni umane 3D.

## <a name="volumetric-video-and-the-pursuit-of-authentic-human-capture"></a>Video volumetrico e ricerca dell'autentica acquisizione umana

Gli esseri umani sono centrali per la narrazione, nel senso più letterale: un parlato umano, un'esecuzione o come soggetto della storia. Alcuni dei momenti più coinvolgenti e accattivanti delle prime esperienze immersive di oggi sono i social network. Dalla condivisione di un'esperienza di realtà mista nel tuo living, alla visualizzazione degli amici in nuovi ambienti straordinari. L'elemento umano rende anche la realtà più fantastica, una realtà.

![Il modo in cui la realtà virtuale è in realtà virtuale](../develop/platform-capabilities-and-apis/images/mindshow-in-vr-640px.jpg)

Gli avatar nelle esperienze immersive consentono un nuovo tipo di realizzazione nella narrazione. Le app più recenti stanno ripassando il concetto di proprietà del corpo virtuale e configurando un salto generazionale nell'eliminare la distanza tra le persone. Aziende come [La maestra stanno](https://mindshow.com/) sviluppando strumenti creativi che sfruttano gli avatar, consentendo agli utenti di assumere personaggi e personaggi completamente nuovi. Altri stanno esplorando metodi di espressione [creativa,](https://en.wikipedia.org/wiki/Uncanny_valley)un'opportunità potenzialmente illimitata per esplorare la natura (e la necessità) degli attributi simili a quello umano. Attualmente, questa assenza di [](https://en.wikipedia.org/wiki/Uncanny_valley) realisticità consente di evitare la sconnessa valle dell'aspetto umano insieme a una serie di problemi tecnici per gli sviluppatori di tutti i giorni. Per questi motivi (e altro ancora) è molto probabile che gli avatar non realistici diventino l'impostazione predefinita per il futuro prevedibile. Tuttavia, mentre il realistico rappresenta un'enorme sfida per la realtà mista, esistono scenari chiave che richiedono una rappresentazione autentica degli esseri *umani nello spazio 3D.*

In Microsoft, un piccolo team di Microsoft Research ha dedicato diversi anni allo sviluppo di un metodo per l'acquisizione di esseri umani tramite una forma di video volumetrico. Il processo oggi è simile alla produzione video: invece di applicare lo spostamento a un asset sculturato, si tratta di una registrazione 3D completa. Le prestazioni e l'immagine vengono acquisite in tempo reale: non è opera di un artista, ma è una rappresentazione autentica. Mentre la tecnologia sta iniziando a espandersi in applicazioni commerciali, le implicazioni del video volumetrico sono fondamentali per la visione di [Microsoft di More Personal Computing.](https://www.youtube.com/watch?v=tcyj-_IEWt8)

![Video volumetrico SIGGRAPH 2015](../develop/platform-capabilities-and-apis/images/volumetric-video-siggraph-2015.gif)

L'acquisizione umana autentica sblocca nuove categorie univoche di esperienze nella realtà mista. Vedere qualcuno che riconosci, che si tratta di una celebrità, di un collega o di una persona amata, crea una profondità di intimità mai prima possibile in un supporto digitale. Il viso, le espressioni, la sfumatura nei movimenti sono tutti parte di ciò che sono. Quali opportunità si sbloccano quando è possibile acquisire queste qualità umane nello spazio 3D?

Oggi il team sta spingendo i limiti del video volumetrico concentrandosi su [](https://www.youtube.com/watch?v=BwWueXlsOrA) settori come l'intrattenimento e l'istruzione: [Actiongram](https://www.microsoft.com/p/actiongram/9nblggh5ftmt) include personaggi creativi e celebrità per creare storie di realtà mista. [Destination: Mars exhibit](https://www.jpl.nasa.gov/news/news.php?feature=6220), now at NASA's Kennedy Space Center, features a volumetric video of il mitico astronauta Rondrin. L'esperienza consente ai visitatori di aggirare la superficie di Marte con Ronzio mentre introduce la ricerca della colonizzazione umana su Marte.

## <a name="humans-are-fundamental-to-mixed-reality"></a>Gli esseri umani sono fondamentali per la realtà mista

La progettazione di modi per far sembrare questi video naturali rappresenta una sfida, ma in cui il team vede enormi potenzialità. Queste opportunità si espanderanno man appena la tecnologia diventa più accessibile e passa dalle registrazioni all'acquisizione in tempo reale.

[Holoportation](https://www.microsoft.com/research/project/holoportation-3/) è un'attività di ricerca basata sulla stessa tecnologia fondamentale, che acquisisce autenticamente informazioni visive e di profondità ed esegue il rendering del risultato in tempo reale. Il team sta esplorando il significato della potenza della rappresentazione umana realistica per il futuro delle conversazioni e delle esperienze condivise. Cosa accade quando un'acquisizione tridimensionale di qualcuno, da qualsiasi parte del mondo, può essere aggiunta all'ambiente?

![Futuro della conversazione](../develop/platform-capabilities-and-apis/images/girl-with-dress.jpg)

Dall'affollamento di un nuovo livello di immersione nelle app quotidiane come Skype, alla modifica radicale del concetto di riunioni digitali e viaggi d'affari. Il video volumetrico apre scenari unici: uno specialista che pratica la formazione dei medici in un continente lontano o di amici digitali che siede sui divani e sulle sedie nel tuo living. L'aggiunta di rappresentazioni umane autentiche alle esperienze di realtà mista rimodella in modo radicale il concetto di riunioni digitali e di viaggi di lavoro.

Proprio come l'arte astratta di James Turrell e il critico realistico di Ai Weiwei offrono le proprie sfide tecniche, anche i metodi per rappresentare gli esseri umani come avatar creativi e acquisizioni realistiche. Uno non può essere ignorato alla luce dell'altro e l'esplorazione del potenziale di ognuno ci aiuterà a comprendere l'interazione umana in questo nuovo spazio.

## <a name="about-the-author"></a>Informazioni sull'autore

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Mark Vitazko" width="60" height="60" src="images/mark-vitazko.jpg"></td>
<td style="border-style: none"><b>Mark Vitazko</b><br>Designer di esperienza utente @Microsoft</td>
</tr>
</table>

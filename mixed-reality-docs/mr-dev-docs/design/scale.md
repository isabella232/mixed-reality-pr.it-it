---
title: Scalabilità
description: Per visualizzare contenuto che sembri realistico in forma olografica, è importante simulare quanto più possibile le statistiche visive del mondo reale.
author: shengkait
ms.author: shentan
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, stile, progettazione, cuffie per realtà mista, auricolare di realtà mista di Windows, auricolare di realtà virtuale, HoloLens, scala, ologrammi
ms.openlocfilehash: 6711a58fb4dde2aa28272c3003e642c4f4d3e236
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/01/2021
ms.locfileid: "97848275"
---
# <a name="scale"></a>Scalabilità

La chiave per la visualizzazione di contenuto olografico realistico è la possibilità di simulare le statistiche visive del mondo reale nel modo più rigoroso possibile. Incorporare indicatori visivi per aiutare gli utenti del mondo reale a comprendere dove si trovano gli oggetti, quanto sono grandi e cosa ne fanno. La scala di un oggetto è uno dei segnali visivi più importanti perché fornisce al Visualizzatore un senso della dimensione degli oggetti e dei segnali alla relativa posizione. Inoltre, la visualizzazione di oggetti su scala reale è uno dei principali elementi di differenziazione per la realtà mista in generale, un elemento che non è stato possibile nella visualizzazione precedente basata sullo schermo.

<br>

---

## <a name="how-to-suggest-the-scale-of-objects-and-environments"></a>Come suggerire la scala di oggetti e ambienti

Esistono diversi modi per suggerire la scala di un oggetto, alcuni dei quali hanno possibili effetti su altri fattori percettivi. Il codice principale è quello di visualizzare gli oggetti con una dimensione "reale" e mantenere le dimensioni realistiche quando gli utenti si spostano. Gli ologrammi prenderanno una quantità diversa di angoli visivi dell'utente di un utente man mano che diventano più vicini o più lontani, allo stesso modo degli oggetti reali.

### <a name="use-the-distance-of-objects-as-theyre-presented-to-the-user"></a>Usa la distanza degli oggetti presentati all'utente

Un metodo comune prevede l'uso della distanza degli oggetti che vengono presentati all'utente. Si consideri, ad esempio, la visualizzazione di un'auto famiglia di grandi dimensioni davanti all'utente. Se la vettura si trovava direttamente davanti alla lunghezza di ARM, sarebbe troppo grande per adattarsi al campo di visualizzazione dell'utente. Gli oggetti Close richiedono che l'utente sposti l'intestazione e il corpo per comprendere l'intero oggetto. Se la macchina viene posizionata più a lungo (attraverso la stanza), l'utente può stabilire un senso di scala visualizzando l'intero oggetto nel campo di visualizzazione. Gli utenti possono quindi spostarsi più vicino all'oggetto per un'ispezione più dettagliata.

:::row:::
    :::column:::
        **[Volvo usa questa tecnica per creare un'](https://www.youtube.com/watch?v=DilzwF90vec)** esperienza di showroom per una nuova macchina, usando la scalabilità dell'automobile olografica in modo da essere realistica e intuitiva per l'utente. L'esperienza inizia con l'ologramma dell'auto in una tabella fisica, consentendo all'utente di comprendere la dimensione e la forma totali del modello. Successivamente, l'auto si espande fino a una scala oltre le dimensioni del campo di visualizzazione del dispositivo. Poiché l'utente ha già acquisito un frame di riferimento dal modello più piccolo, può spostarsi in modo adeguato sulle funzionalità dell'auto.<br>
        <br>
        *Immagine: esperienza Volvo Cars per HoloLens*
    :::column-end:::
        :::column:::
       ![Esperienza Volvo Cars per HoloLens](images/volvo-cars-microsoft-hololens-experience01-640px.jpg)<br>
    :::column-end:::
:::row-end:::


<br>

---

### <a name="use-holograms-to-modify-the-users-real-space"></a>Usare gli ologrammi per modificare lo spazio reale dell'utente

Un altro metodo consiste nell'usare gli ologrammi per modificare lo spazio reale dell'utente, sostituendo i muri o i soffitti esistenti con gli ambienti o aggiungendo "holes" o "Windows". In questo modo, gli oggetti over-size possono sembrare "break-through" nello spazio fisico. Un albero di grandi dimensioni, ad esempio, potrebbe non rientrare nella maggior parte dei salotti degli utenti, ma mettendo un cielo virtuale sul soffitto, lo spazio fisico si espande nel computer virtuale. Ciò consente all'utente di spostarsi sulla base dell'albero virtuale e di raccogliere un senso di scalabilità e aspetto reale. Gli utenti possono quindi cercare di estendersi oltre lo spazio fisico della stanza.

:::row:::
    :::column:::
        **[Minecraft ha sviluppato un'esperienza concettuale](https://minecraft.net/)** con una tecnica simile. Aggiungendo una finestra virtuale a una superficie fisica, gli oggetti esistenti nella stanza vengono inseriti nel contesto di un ambiente notevolmente più ampio, oltre i limiti della scala fisica della stanza.<br>
        <br>
        *Immagine: esperienza del concetto di Minecraft per HoloLens*
    :::column-end:::
        :::column:::
       ![Esperienza del concetto Minecraft per HoloLens](images/800px-minecraftwindow-640px.jpg)<br><br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="experimenting-with-scale"></a>Sperimentazione con scalabilità

Le finestre di progettazione hanno sperimentato la modifica della scala modificando le dimensioni ' reali ' visualizzate dell'oggetto. Allo stesso tempo, mantengono una posizione di un singolo oggetto per approssimare un oggetto che si sposta verso il Visualizzatore senza alcuno spostamento effettivo. Questa operazione è stata testata in alcuni casi come un modo per simulare la visualizzazione di elementi più vicini, rispettando al contempo le potenziali limitazioni di comfort della visualizzazione di contenuto virtuale più vicino alla "zona di comfort" suggerita.

Questa operazione può tuttavia creare alcuni artefatti possibili nell'esperienza:
* Per gli oggetti virtuali che rappresentano un oggetto con una dimensione "nota" al visualizzatore, la modifica della scala senza modificare la posizione comporta segnali visivi in conflitto. Gli occhi possono comunque "vedere" l'oggetto a una certa profondità a causa di suggerimenti vergence. Per altre informazioni, vedere l'articolo [comfort](comfort.md) . La dimensione funge da spunto monoculare che l'oggetto potrebbe avvicinarsi più vicino. Questi segnali in conflitto portano a percezioni confuse: i visualizzatori spesso visualizzano l'oggetto che rimane sul posto (a causa del segnale di profondità costante) ma cresce rapidamente.
* In alcuni casi, la modifica della scala viene invece considerata come una cue "incombente", in cui l'oggetto può essere visualizzato o meno per modificare la scala da un visualizzatore, ma sembra essere spostato direttamente verso gli occhi del visualizzatore, che può essere una sensazione scomoda.
* Con le aree di confronto nel mondo reale, tali modifiche di ridimensionamento vengono talvolta considerate come la modifica della posizione lungo più assi. gli oggetti sembrano essere ridotti anziché essere più vicini (simili in una proiezione 2D di spostamento 3D in alcuni casi).
* Infine, per gli oggetti senza una dimensione ' reale del mondo ' nota (ad esempio, forme arbitrarie con dimensioni arbitrarie, elementi dell'interfaccia utente e così via), la modifica della scala può agire funzionalmente come un modo per simulare le modifiche a distanza. I visualizzatori non dispongono di un numero così elevato di suggerimenti dall'alto verso il basso per comprendere la dimensione o la posizione reale dell'oggetto, in modo che la scala possa essere elaborata come una cue più importante.

<br>

---

## <a name="see-also"></a>Vedi anche
* [Colore, luce e materiali](../color,-light-and-materials.md)
* [Tipografia](typography.md)
* [Progettazione dell'audio spaziale](spatial-sound-design.md)

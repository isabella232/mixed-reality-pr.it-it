---
title: Scalabilità
description: Per visualizzare contenuto che sembri realistico in forma olografica, è importante simulare quanto più possibile le statistiche visive del mondo reale.
author: shengkait
ms.author: shentan
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, style, design, visore per realtà mista, visore windows mixed reality, visore per realtà virtuale, HoloLens, scala, ologrammi
ms.openlocfilehash: 0b643b7f4b53795afa6bac9b54e55565233ac1d96a6a58d5389a8a4b7db8d7cc
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115223009"
---
# <a name="scale"></a>Scalabilità

La chiave per visualizzare contenuto olografico realistico è simulare il più possibile le statistiche visive del mondo reale. Incorporare segnali visivi per aiutare gli utenti reali a comprendere dove sono gli oggetti, le loro grandi e le loro proprietà. La scala di un oggetto è uno dei segnali visivi più importanti perché offre al visualizzatore un'idea delle dimensioni degli oggetti e dei segnali alla relativa posizione. Inoltre, la visualizzazione di oggetti su scala reale è uno dei principali fattori di differenziazione dell'esperienza per la realtà mista in generale, cosa che non è stata possibile nella visualizzazione precedente basata su schermo.

<br>

---

## <a name="how-to-suggest-the-scale-of-objects-and-environments"></a>Come suggerire la scalabilità di oggetti e ambienti

Esistono molti modi per suggerire la scala di un oggetto, alcuni dei quali hanno possibili effetti su altri fattori percettivi. La chiave è visualizzare gli oggetti con dimensioni "reali" e mantenere le dimensioni realistiche quando gli utenti si spostano. Ologrammi l'angolo visivo di un utente diverso man appena si avvicina o si allontana, come fanno gli oggetti reali.

### <a name="use-the-distance-of-objects-as-theyre-presented-to-the-user"></a>Usare la distanza degli oggetti quando vengono presentati all'utente

Un metodo comune è usare la distanza degli oggetti quando vengono presentati all'utente. Ad esempio, è consigliabile visualizzare un'auto di grandi dimensioni di famiglia davanti all'utente. Se l'auto si trovasse direttamente davanti alla lunghezza del braccio, sarebbe troppo grande per adattarsi al campo di visualizzazione dell'utente. Gli oggetti close richiedono all'utente di spostare la testa e il corpo per comprendere l'intera parte dell'oggetto. Se l'auto è posizionata più lontano (dall'altra parte della stanza), l'utente può stabilire un senso di scala visualizzando l'intero oggetto nel campo di visualizzazione. Gli utenti possono quindi avvicinarsi all'oggetto per un'ispezione più dettagliata.

:::row:::
    :::column:::
        **[Per creare un'esperienza](https://www.youtube.com/watch?v=DilzwF90vec)** di showroom per una nuova auto, Halee ha usato questa tecnica, usando la scala dell'auto olografica in modo realistico e intuitivo per l'utente. L'esperienza inizia con l'ologramma dell'auto su una tabella fisica, consentendo all'utente di comprendere le dimensioni totali e la forma del modello. Più avanti nell'esperienza, l'auto si espande fino a una scala superiore alle dimensioni del campo di visualizzazione del dispositivo. Poiché l'utente ha già acquisito un frame di riferimento dal modello più piccolo, può esplorare in modo adeguato le caratteristiche dell'auto.<br>
        <br>
        *Immagine: Esperienza di Automobili Di Automobili per HoloLens*
    :::column-end:::
        :::column:::
       ![Esperienza di Automobili Di Automobili per HoloLens](images/volvo-cars-microsoft-hololens-experience01-640px.jpg)<br>
    :::column-end:::
:::row-end:::


<br>

---

### <a name="use-holograms-to-modify-the-users-real-space"></a>Usare gli ologrammi per modificare lo spazio reale dell'utente

Un altro metodo è usare gli ologrammi per modificare lo spazio reale dell'utente, sostituendo le pareti o i controsoffitti esistenti con ambienti o aggiungendo "fori" o "finestre". Ciò consente agli oggetti con dimensioni troppo grandi di "sfondare" lo spazio fisico. Ad esempio, un albero di grandi dimensioni potrebbe non rientrare nei living della maggior parte degli utenti, ma mettendo un cielo virtuale sul loro tetto, lo spazio fisico si espande nel virtuale. Ciò consente all'utente di aggirare la base dell'albero virtuale e raccogliere un senso di scala e di aspetto reale. Gli utenti possono quindi cercare per vedere che si estendono ben oltre lo spazio fisico della stanza.

:::row:::
    :::column:::
        **[Minecraft ha sviluppato un concetto di esperienza](https://minecraft.net/)** usando una tecnica simile. Aggiungendo una finestra virtuale a una superficie fisica, gli oggetti esistenti nella stanza vengono posizionati nel contesto di un ambiente molto più grande, oltre le limitazioni di scala fisica della stanza.<br>
        <br>
        *Immagine: Minecraft'esperienza di concetto per HoloLens*
    :::column-end:::
        :::column:::
       ![Minecraft'esperienza di concetto per HoloLens](images/800px-minecraftwindow-640px.jpg)<br><br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="experimenting-with-scale"></a>Sperimentazione della scalabilità

I progettisti hanno sperimentato la modifica della scala modificando le dimensioni "reali" visualizzate dell'oggetto. Allo stesso tempo, mantengono una singola posizione dell'oggetto per approssimare un oggetto che si sposta verso il visualizzatore senza alcun movimento effettivo. Questa operazione è stata testata in alcuni casi come un modo per simulare la visualizzazione da vicino degli elementi, rispettando al tempo stesso le potenziali limitazioni di comfort della visualizzazione del contenuto virtuale più vicino rispetto a quanto suggerito dalla "zona di comfort".

Ciò può tuttavia creare alcuni elementi possibili nell'esperienza:
* Per gli oggetti virtuali che rappresentano un oggetto con una dimensione "nota" per il visualizzatore, la modifica della scala senza modificare la posizione comporta segnali visivi in conflitto. Gli occhi possono comunque "vedere" l'oggetto a una certa profondità a causa di segnali di vergence. Per altre informazioni, vedere [l'articolo Comfort.](comfort.md) La dimensione funge da segnale monocolare che l'oggetto potrebbe essere sempre più vicino. Questi segnali in conflitto conducono a percezioni confuse: gli utenti spesso vedono l'oggetto come in posizione (a causa del segnale di profondità costante) ma in rapida crescita.
* In alcuni casi, il cambiamento di scala viene invece visto come un segnale di "incombente", in cui l'oggetto può o non può essere visto cambiare scala da un visualizzatore, ma sembra essere in movimento direttamente verso gli occhi dello visualizzatore (che può essere una grande emozione).
* Con le superfici di confronto nel mondo reale, tali modifiche di ridimensionamento vengono talvolta viste come una modifica della posizione lungo più assi. Gli oggetti sembrano scendere più in basso invece di avvicinarsi (in alcuni casi, in una proiezione 2D di spostamento 3D).
* Infine, per gli oggetti senza dimensioni note del "mondo reale", ad esempio forme arbitrarie con dimensioni arbitrarie, elementi dell'interfaccia utente e così via, la modifica della scala può fungere da modo funzionale per simulare i cambiamenti in distanza. I visualizzatori non hanno un numero di segnali dall'alto verso il basso preesiste per comprendere la vera dimensione o posizione dell'oggetto, quindi la scala può essere elaborata come un segnale più importante.

<br>

---

## <a name="see-also"></a>Vedi anche
* [Colore, luce e materiali](./color-light-and-materials.md)
* [Tipografia](typography.md)
* [Progettazione dell'audio spaziale](spatial-sound-design.md)